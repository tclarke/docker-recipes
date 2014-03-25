Supervisor (a Docker image)
===========================

Available on the [Docker index] (https://index.docker.io/) as **quintenk/supervisor**

Based on centos 6.5

Supervisor is a linux process manager ([Supervisor website](http://supervisord.org/ "Supervisor website")). It allows us to start containers with e.g.
- multiple processes
- a deamon / background process
- launch groups of processes in a specific order
- and more advanced stuff

This image is intended to be built on. Therefore, a child Dockerfile should not have to upgrade centos.

To make easy use of supervisor, an inheriting Docker project should contain one or more files `[SOME_NAME].conf` and add those to /etc/supervisor/conf.d in the Dockerfile. Note that you can find examples of such files in this repositories projects. Personally, I name all my supervisor configuration file [SERVICE].sv.conf for clarity.

To run supervisor, you can add `CMD supervisord -c /etc/supervisor.conf`.


Heritage
========
Based on the ubuntu 12.04 LTS supervisord image created by [Krijger](https://github.com/Krijger/docker-cookbooks).
