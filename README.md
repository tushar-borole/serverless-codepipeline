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



### Some details on these parameters
Parameter | Info | Default | More Information
------ | ------ | ------ | ------
image (node) | If the runtime is nodeJS | aws/codebuild/nodejs:6.3.1 | [Lookup other image identifiers](http://docs.aws.amazon.com/codebuild/latest/userguide/build-env-ref-available.html)
image (python) | If the runtime is python | aws/codebuild/python:3.5.2 | [Lookup other image identifiers](http://docs.aws.amazon.com/codebuild/latest/userguide/build-env-ref-available.html)
image (other) | If the runtime is something else | aws/codebuild/ubuntu-base:14.04 | [Lookup other image identifiers](http://docs.aws.amazon.com/codebuild/latest/userguide/build-env-ref-available.html)
branch | The git branch CodePipeline monitors | master | [More on how CodePipeline starts](http://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-about-starting.html)
owner | The owner of the GitHub repository | *blank* | Required as no default
repository | The GitHub repository CodePipeline monitors | The name of your service | [More on how CodePipeline starts](http://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-about-starting.html)
githubtoken | The GitHub OAuth token for private repos | *blank* | [How to get a token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)
excludestages | Stages you don't want CICD for | *blank* | [Serverless stages](https://serverless.com/framework/docs/providers/aws/guide/workflow#using-stages)




----------

## Contributing

Open an issue first to discuss potential changes/additions. If you have questions with the guide, feel free to leave them as issues in the repository. If you find a typo, create a pull request. The idea is to keep the content up to date and use github’s native feature to help tell the story with issues and PR’s, which are all searchable via google. Why? Because odds are if you have a question, someone else does too! You can learn more here at about how to contribute.

*By contributing to this repository you are agreeing to make your content available subject to the license of this repository.*

### Process
    1. Discuss the changes in a GitHub issue.
    2. Open a Pull Request, reference the issue, and explain the change and why it adds value.
    3. The Pull Request will be evaluated and either merged or declined.

## License

 Use this guide. Attributions are appreciated._

### Copyright

Copyright (c) 2014-2015 [Tushar Borole](http://www.tusharborole.com)

### (The MIT License)
Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### Last but not least
This is made in San Francisco with love and passion  ʕ´•ᴥ•`ʔ

<a href="../../" target="_blank"><img src="https://upload.wikimedia.org/wikipedia/en/thumb/a/a4/Flag_of_the_United_States.svg/440px-Flag_of_the_United_States.svg.png" height="200"></a>
