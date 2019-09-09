# Python Project Template

## Usage

```sh
mkdir project1 && cd project1
wget https://github.com/ichuan/python_project_template/archive/master.tar.gz -O - | tar --strip-components 1  -xf -
```


## Project initialize

```sh
python3 -m venv env
source env/bin/activate
pip install -r requirements.txt

cp config/supervisord.example.ini config/supervisord.ini
```


## Using and managing supervisord

```sh
# start
supervisord -c config/supervisord.ini

# managing
supervisorctl -c config/supervisord.ini
```


## Developing a python package

- First, you need a `setup.py`, simplly get it from [navdeep-G/setup.py](https://github.com/navdeep-G/setup.py):

    ```sh
    curl -OL https://raw.githubusercontent.com/navdeep-G/setup.py/master/setup.py
    ```

- Then, orginze your codes in a sub-dir of project name, like `project1`.
- Install your project locally:

    ```sh
    pip install -e .
    ```

- During developing, you can use both absolute and relative importing like:

    ```python
    from project1.consts import NAME
    from ..consts import NAME
    ```

- Running your project:
  - Import from outside scripts, or
  - Use `python -m project1.main`


## FAQ
- `PermissionError: [Errno 13] error while attempting to bind on address ('0.0.0.0', 443): permission denied`
  - ```sudo setcap 'cap_net_bind_service=+ep' `readlink -f $(which python)` ```
