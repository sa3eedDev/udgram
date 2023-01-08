# Pipeline

The pipleline have three phases, the first one is build, which install the dependencies, lint the code, and build it. The Second phase is an aproval before deploying the the app. The last phase is deploying the app to AWS services. 

We use circleCI for CI and CD.

## Build

For the build first we install Node 14, after that we install the frontend and api dependencies. After that we lint the code and check for any errors. Lastly we build both the frontend and the api

## Approval

After the build is succssfully finished we have to do a manual approval to continue to the deployment phase.

## Deploy 

After we approve the deployment circleCI will install AWS cli and EB cli, to run the deployment commands. **Make sure you enter AWS credentials in the circleCI project enviroment variables.