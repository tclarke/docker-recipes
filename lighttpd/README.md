Lighttpd base image
====================
Lighttpd with fastcgi for connection to other docker containers running fastcgi.
Create a derived image with lighttpd config files for all connected containers (see the sample) which will be treating as docker linked servers.

Run each application container first, exporting the static directory:
   docker run -d -v /var/www/django/static myuser/myapp

NOTE: if you instend to front multiple django app containers, you must change the django settings to use `myapp-static` instead of `static` so you can export a separate static files directory for each application.

Now run your sub-image and link to your static files (and exporting ports to the local host):
   docker run -d -P --link=MyApp:MyApp --volumes-from=MyApp myname/webproxy

`MyApp` will correspond to the lighttpd config `env.MYAPP_` variables.
