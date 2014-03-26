Django docker recipe
====================
Django app container using supervisord.
Served via lighttpd and fastcgi.
Includes support for celery and south.

To create an app, you'll need to add your django app path and lighttpd conf file (based on the sample) like this:

   ADD myapp /var/www/django/myapp
   ADD myapp.conf /etc/lighttpd/apps.conf.d/

You may also need to initialize your app's database, something like this usually does the trick:
   WORKDIR /var/www/django/myapp
   RUN ./manage.py syncdb --noinput
   RUN ./manage.py migrate --noinput

   # optional step to preload a database. You'll need to do this if you have the admin system enabled in order to create the admin user
   RUN ./manage.py loaddata initial_db.json

