# serverless-plugin-kong

[Serverless framework](https://www.serverless.com) plugin to configure a Kong API Gateway cluster.

## Installation

```bash
$ npm install @tropos/serverless-plugin-kong
```

## Usage

Add the plugin to `serverless.yml`

```yaml
# serverless.yml

plugins:
  - serverless-plugin-kong
```

Add an event of type `kong` to your functions in `serverless.yml`. Configure the route with the `route` property. The `aws-lambda` plugin will be automatically configured.

```yaml
# serverless.yml

service: example

functions:
  hello:
    handler: handler.hello
    events:
      - kong:
          route:
            methods:
              - GET
            paths:
              - /
            protocols:
              - http
```

Add configuration options to custom section of `serverless.yml`.

```yaml
# serverless.yml
custom:
  kong:
    admin_api_url: http://localhost:8001
    lambda:
      config:
        aws_key: ${env:AWS_ACCESS_KEY_ID, 'asdf'}
        aws_secret: ${env:AWS_SECRET_ACCESS_KEY, 'asdf'}
```

## Contributing

Pull requests welcome! Please fork the repo and submit your PR.
