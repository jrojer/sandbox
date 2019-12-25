
## Sources
 * https://pipenv.readthedocs.io/en/latest/install/
 * https://code.visualstudio.com/docs/python/tutorial-flask

## Environment setup
 * `pip install --user pipenv`  
 * `export PIPENV_VENV_IN_PROJECT=1` in your .bashrc  
 * `cd` into project directory
 * `pipenv install flask`
 * select python interpreter which is in ./.venv.
 * add `configuration` to project's `launch.json`:
   ```json
   {
       "name": "Python: Flask",
       "type": "python",
       "request": "launch",
       "module": "flask",
       "env": {
           "FLASK_APP": "app.py",
           "FLASK_ENV": "development",
           "FLASK_DEBUG": "0"
       },
       "args": [
           "run",
           "--no-debugger",
           "--no-reload"
       ],
       "jinja": true
   },
   ```

## Test
Add the file `app.py`:
```python
from flask import Flask, escape, request
app = Flask(__name__)

@app.route('/')
def hello():
   name = request.args.get("name", "World")
   return 'Hello {}!'.format(escape(name))

```
Debugger (`F5`) should work properly.


