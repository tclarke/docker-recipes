Django docker recipe
====================
Django app container using supervisord.
Serves fastcgi and can be linked to `tclarke/lighttpd`
Includes support for celery and south. (celery worker not running and no redis, just `python-celery`)

To create an app, you'll need to add your django app path and lighttpd conf file (based on the sample) like this:
   ADD myapp /var/www/django

You may also need to initialize your app's database, something like this usually does the trick:
   WORKDIR /var/www/django
   RUN ./manage.py syncdb --noinput
   RUN ./manage.py migrate --noinput

   # optional step to preload a database. You'll need to do this if you have the admin system enabled in order to create the admin user
   RUN ./manage.py loaddata initial_db.json

   # collect static files
   RUN ./manage.py collectstatic --noinput

   # expose the FastCGI port
   EXPORT 9123
