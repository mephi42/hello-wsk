# Useful links
* Check that you have an organization and a space: https://console.bluemix.net/account/organizations
* Download CLI: https://console.bluemix.net/docs/cli/reference/ibmcloud/download_cli.html#install_use
* Read HOWTO: https://console.bluemix.net/docs/openwhisk/openwhisk_actions.html#creating-docker-actions

# TL;DR
    1$ ibmcloud login
    2$ ibmcloud target -r eu-gb --cf  # A region must match a space!
    3$ ibmcloud fn action create hello-wsk --docker mephi42/hello-wsk

    4$ docker build -t mephi42/hello-wsk .
    5$ docker run -it --rm mephi42/hello-wsk /action/exec '{"foo": "bar"}'
    6$ docker push mephi42/hello-wsk
    7$ ibmcloud fn action update hello-wsk --docker mephi42/hello-wsk
    8$ ibmcloud fn action invoke --result hello-wsk --param foo bar
    # goto 4
