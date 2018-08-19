# OpenWhisk "Hello, World!" with a stand-alone private .zip file

## Summary
Publish an image on [IBM Cloud Container Registry](https://console.bluemix.net/containers-kubernetes/registry/private) and run it as an [IBM Cloud Function](https://console.bluemix.net/openwhisk).

Does not require disclosing the code.

Code must be compatible with the default `openwhisk/dockerskeleton` image and [be smaller than 48 MB](https://console.bluemix.net/docs/openwhisk/openwhisk_reference.html#openwhisk_syslimits_codesize).

## Useful links
* [.zip file HOWTO](https://www.ibm.com/blogs/bluemix/2017/01/docker-bluemix-openwhisk)

## TL;DR

    1$ ibmcloud fn action create hello-wsk --docker openwhisk/dockerskeleton

    2$ (cd fs/action && zip -r - *) >binary.zip
    3$ ibmcloud fn action update hello-wsk binary.zip --docker openwhisk/dockerskeleton
    4$ ibmcloud fn action invoke --result hello-wsk --param foo bar
    # goto 2
