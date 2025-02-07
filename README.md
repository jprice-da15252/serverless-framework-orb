# serverless-framework Orb
[![CircleCI Build Status](https://circleci.com/gh/jprice-da15252/serverless-framework-orb.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/jprice-da15252/serverless-framework-orb) [![CircleCI Orb Version](https://img.shields.io/badge/endpoint.svg?url=https://badges.circleci.io/orb/jprice-da15252/serverless-framework)](https://circleci.com/orbs/registry/orb/jprice-da15252/serverless-framework) [![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/jprice-da15252/serverless-framework-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

Use the Serverless Framework orb for CircleCI to easily deploy to your favorite cloud platform.


## Usage

Example use-cases are provided on the orb [registry page](https://circleci.com/orbs/registry/orb/jprice-da15252/serverless-framework#usage-examples). Source for these examples can be found within the `src/examples` directory.

**Example**
Use the Serverless Framework orb's **_"setup"_** command to install the Serverless Framework CLI and authenticate with your account if an API key is provided. This example shows how to construct a custom "deploy" job using the Serverless and AWS CLI orbs to deploy an app to AWS.

```yaml
  version: 2.1
  orbs:
    serverless: jprice-da15252/serverless-framework@x.y
    aws-cli: circleci/aws-cli@x.y
  jobs:
    deploy:
      executor: serverless/default
      steps:
        - checkout
        - aws-cli/setup
        - serverless/setup:
            app-name: serverless-framework-orb
            org-name: circleci
        - run:
            name: deploy
            command: serverless deploy -v
  workflows:
    deploy:
      jobs:
        - deploy

```

View your deployments at https://dashboard.serverless.com/

## Resources

[CircleCI Orb Registry Page](https://circleci.com/orbs/registry/orb/jprice-da15252/serverless-framework) - The official registry page of this orb for all versions, executors, commands, and jobs described.  
[CircleCI Orb Docs](https://circleci.com/docs/2.0/orb-intro/#section=configuration) - Docs for using and creating CircleCI Orbs.  

### How To Contribute

We welcome [issues](https://github.com/jprice-da15252/serverless-framework-orb/issues) to and [pull requests](https://github.com/jprice-da15252/serverless-framework-orb/pulls) against this repository!

To publish a new production version:
* Create a PR to the `Alpha` branch with your changes. This will act as a "staging" branch.
* When ready to publish a new production version, create a PR from `Alpha` to `master`. The Git Subject should include `[semver:patch|minor|release|skip]` to indicate the type of release.
* On merge, the release will be published to the orb registry automatically.

For further questions/comments about this or other orbs, visit the Orb Category of [CircleCI Discuss](https://discuss.circleci.com/c/orbs).
