FROM node:14.5.0-alpine3.12
# Install packages and properties needed by the app
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
# directory of application
WORKDIR /home/node/app
# copy application files ./ to /home/node/app
COPY app/ ./
# user node
USER node
# run npm install
RUN npm install
# run npm start
EXPOSE 8080
# define commands to run when the container starts
CMD ["node", "app"]
