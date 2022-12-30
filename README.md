# AWS front/backend example

We'll setup a serverless example:
- Cloudformation YML script to set up the serverless infrastrcuture
  - AWS Lambda Function
  - AWS Gateway to create a REST API on top of the Lambda Function
- Hello World `index.html` which calls this REST API

## Setup:
```
$ cd aws-lambda && npm install
$ cd frontend && npm install
```
see [aws-lambda/README.md](aws-lambda/README.md) for instructions to setup AWS CLI and your `~/.aws/credentials`.

## Run it:
Deploy the REST API:
```
$ cd aws-lambda
$ npm run create      # or update or delete or monitor
```

Serve the frontend:  see `frontend/README.md`
```
$ cd frontend
$ npm start

# then open the URL listed  e.g. http://127.0.0.1:8081
```

Edit `index.html` with the URL to your REST API.
```
$ cd aws-lambda
$ npm run stats        # gives the URL of your service
                       # something like
                       # `https://4xkbm7p24a.execute-api.us-west-2.amazonaws.com/dev/hello_world`

```
- Then, paste `<URL>/hello_world` into your `index.html`
- Then reload the page

## Credits, More Reading:
The serverless REST API is created using the rest-api cloudformation script from:
- https://github.com/upload-io/cloudformation-lambda-examples
