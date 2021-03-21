FROM node:12.16.1-alpine3.11

# set working directory
WORKDIR /frontend

# add `/app/node_modules/.bin` to $PATH
ENV PATH /frontend/node_modules/.bin:$PATH

# install and cache app dependencies
COPY package*.json ./
RUN yarn install

COPY . .

# start app
EXPOSE 3000
CMD ["yarn", "dev"]