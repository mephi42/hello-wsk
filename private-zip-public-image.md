# OpenWhisk "Hello, World!" with a private .zip file in a public Docker image

## Useful links
* [Large applications HOWTO](http://jamesthom.as/blog/2017/08/04/large-applications-on-openwhisk)

## TL;DR

    1$ docker build -t mephi42/hello-wsk2 image2
    2$ docker push mephi42/hello-wsk2
    3$ (cd private-code && zip -r - *) >binary2.zip
    4$ ibmcloud fn action update hello-wsk2 binary2.zip --docker mephi42/hello-wsk2
    5$ ibmcloud fn action invoke --result hello-wsk2 --param "node 1" "node 3"
    # goto 1 or 3
