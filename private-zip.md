# OpenWhisk "Hello, World!" with a stand-alone private .zip file

## Summary
Publish an image on [IBM Cloud Container Registry](https://console.bluemix.net/containers-kubernetes/registry/private) and run it as an [IBM Cloud Function](https://console.bluemix.net/openwhisk).

## Useful links
* [.zip file HOWTO](https://www.ibm.com/blogs/bluemix/2017/01/docker-bluemix-openwhisk)

## TL;DR

    1$ ibmcloud fn action create hello-wsk --docker openwhisk/dockerskeleton

    2$ (cd fs/action && zip -r - *) >binary.zip
    3$ ibmcloud fn action update hello-wsk binary.zip --docker openwhisk/dockerskeleton
    4$ ibmcloud fn action invoke --result hello-wsk --param foo bar
    # goto 2
