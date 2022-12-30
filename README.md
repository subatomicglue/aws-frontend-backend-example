# AWS front/backend example

We'll setup a serverless example:
- Cloudformation YML script to set up the serverless infrastrcuture
  - AWS Lambda Function
  - AWS Gateway to create a REST API on top of the Lambda Function
- Hello World `index.html` which calls this REST API

## Setup:
```
$ cd aws-lambda && npm install; cd -
$ cd frontend && npm install; cd -
```
see [aws-lambda/README.md](aws-lambda/README.md) for instructions to setup AWS CLI and your `~/.aws/credentials`.

## Run it:
Deploy the REST API:
```
$ cd aws-lambda && npm run create       # or update|delete|monitor|stats
```

Then, retrieve your REST API's URL:
```
$ npm run stats

# gives the URL of your service
# something like https://4xkbm7p24a.execute-api.us-west-2.amazonaws.com/dev
```
- Then paste `<URL>/hello_world` into [frontend/src/index.html](frontend/src/index.html)


Serve the frontend:
```
$ cd frontend && npm start

# then open the URL listed  e.g. http://127.0.0.1:8081
```

## Credits, More Reading:
The serverless REST API is created using the rest-api cloudformation script from:
- https://github.com/upload-io/cloudformation-lambda-examples

