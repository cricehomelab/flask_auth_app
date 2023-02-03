Working through tutorial from this location.
https://www.digitalocean.com/community/tutorials/how-to-add-authentication-to-your-app-with-flask-login

Using this as research for other project.

2/3/22 - something weird in this tutorial about creating the DB. It has us doing this from the python REPL and running the following 
two lines of code

    from project import db, create_app, models
    db.create_all(app=create_app())

This line fails with this error:
    >>> db.create_all(app=create_app())
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: SQLAlchemy.create_all() got an unexpected keyword argument 'app'


Attempted this to create this.
    >>> db.create_all()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      File "C:\Users\charl\Desktop\flask_auth_app\.venv\lib\site-packages\flask_sqlalchemy\extension.py", line 884, in create_all
        self._call_for_binds(bind_key, "create_all")
      File "C:\Users\charl\Desktop\flask_auth_app\.venv\lib\site-packages\flask_sqlalchemy\extension.py", line 855, in _call_for_binds
        engine = self.engines[key]
      File "C:\Users\charl\Desktop\flask_auth_app\.venv\lib\site-packages\flask_sqlalchemy\extension.py", line 636, in engines
        app = current_app._get_current_object()  # type: ignore[attr-defined]
      File "C:\Users\charl\Desktop\flask_auth_app\.venv\lib\site-packages\werkzeug\local.py", line 513, in _get_current_object
        raise RuntimeError(unbound_message) from None
    RuntimeError: Working outside of application context.

    This typically means that you attempted to use functionality that needed
    the current application. To solve this, set up an application context
    with app.app_context(). See the documentation for more information.

as best as I can tell we have already specified the context in our __init__.py with 
    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///db.sqlite'

From some reading it looks like there might be a different way to do this now as this tutorial is about 4 years old now.

Going to look for some different resources on this.