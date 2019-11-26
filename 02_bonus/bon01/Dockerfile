FROM ubuntu

RUN \
	apt-get update \
	&& apt-get upgrade -y \
	&& apt-get install python3 python3-pip -y \
	&& pip3 install Django

RUN \
	django-admin startproject django_app

WORKDIR django_app

RUN \
	python3 manage.py migrate \
	&& python3 manage.py createsuperuser \
	&& echo "ALLOWED_HOSTS = ['10.12.3.7']" >> django_app/settings.py
ENTRYPOINT python3 manage.py runserver 0.0.0.0:8000

