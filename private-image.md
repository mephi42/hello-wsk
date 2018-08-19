# OpenWhisk "Hello, World!" with a private Docker image

## Summary
Publish an image on [IBM Cloud Container Registry](https://console.bluemix.net/containers-kubernetes/registry/private) and run it as an [IBM Cloud Function](https://console.bluemix.net/openwhisk).

Does not require disclosing the code.

Does not work yet due to OpenWhisk technical limitations.

## Useful links
* [Private registry HOWTO](https://console.bluemix.net/docs/services/Registry/index.html#index)

## TL;DR
    $ ibmcloud plugin install container-registry -r Bluemix
    $ ibmcloud cr login
    $ ibmcloud cr namespace-add mephi42

    $ docker build -t registry.ng.bluemix.net/mephi42/hello-wsk .
    $ docker push registry.ng.bluemix.net/mephi42/hello-wsk
