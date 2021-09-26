# Python Project Template
Simple python project template, suitable for standalone (non Django) or lightweight (like sanic/flask), with supervisord in consideration

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

- First, orginze your codes in a sub-dir of project name, like `project1`.
- We already included a `setup.py` from [navdeep-G/setup.py](https://github.com/navdeep-G/setup.py), simply modify it.
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

- Building python packages:
  - Install setuptools: `pip install setuptools wheel`
  - Build: `python setup.py bdist_wheel`
  - `dist/*.whl` will be the compiled package


## FAQ
- `PermissionError: [Errno 13] error while attempting to bind on address ('0.0.0.0', 443): permission denied`
  - ```sudo setcap 'cap_net_bind_service=+ep' `readlink -f $(which python)` ```
