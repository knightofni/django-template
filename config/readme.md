# Ready to use template to start django project with good settings

using [this wonderfil project](https://github.com/pydanny/cookiecutter-django) as a base.

Changed :
    - Removed some dependencies for easier start (removed django-secure, s3 static files hosting)
    - Checked how to deploy this project with dokku 
        - read config/install.rst
        - added a .env file to force dokku to build with buildpacks 
    - Changed the local settings to use sqlite (postgres kept for deploy)
