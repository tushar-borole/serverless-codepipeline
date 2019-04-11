# serverless-codepipeline
Add CI CD to your serverless application instantly

### Getting Started

```
yarn add serverless-codepipeline
```

add plugin to the serverless.yml

```
plugins:
  modules:
    - serverless-codepipeline
```

Add following configuration in serverless.yml file
```
custom:
  cicd:
    branch: 'master'
    owner: '${REPOSITORY OWNER}'
    repository: '${REPOSITORY NAMW}'
    githubtoken: 'asdas'
    policy: '{
               "Version": "2012-10-17",
               "Statement": [
                 {
                   "Effect": "Allow",
                   "Action": [
                     "elasticbeanstalk:*"
                   ],
                   "Resource": "*"
                 }
               ]
             }'
```

Add buildspec.yml to folder, codebuild use buildspec.yml to deploy application
most common example of buildspec.yml is

```
version: 0.1
phases:
  install:
    commands:
      - npm install
      - npm install -g serverless
  build:
    commands:
      - serverless deploy --stage prod
```
