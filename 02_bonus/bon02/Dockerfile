FROM node

RUN \
	npm install -g create-react-app \
	&& create-react-app app \
	&& npm init -y

WORKDIR app
ENTRYPOINT npm start

#port 3000

