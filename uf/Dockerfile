# root password:    unifield
# docker user:      docker
# docker password:  docker
# psql user:        docker
# psqlpassword:     docker
#
FROM tempo/ufbuntu:10.04

MAINTAINER Vincent GREINER, vg@tempo-consulting.fr


# base packages
USER root
RUN apt-get install -y \
    build-essential \
    bzr \
    ipython \
    python-argparse \
    python-dev 

# dependancies: OpenERP 
RUN apt-get install -y \
    python \
    python-psycopg2 \
    python-reportlab \
    python-egenix-mxdatetime \
    python-tz \
    python-pychart \
    python-pydot \
    python-lxml \
    python-libxslt1 \
    python-vobject \
    python-imaging \
    python-profiler \
    python-setuptools python-yaml \
    python-ldap \
    python-cherrypy3 \
    python-mako \
    python-simplejson \
    python-formencode \
    python-pybabel \
    flashplugin-nonfree \
    python-pip
RUN pip install openerp-client-lib==1.0.3
RUN pip install oerplib

# dependancies: psql client
RUN apt-get install -y postgresql-client-8.4

# dependancies: 7z files
RUN easy_install pylzma


EXPOSE 8061
USER docker
WORKDIR /home/docker
CMD [ "/bin/bash" ]
