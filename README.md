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

# Debugging

    $ ibmcloud fn activation list
    $ ibmcloud fn activation logs <id>

# Private images

Warning: this does not work yet.

    $ ibmcloud plugin install container-registry -r Bluemix
    $ ibmcloud cr login
    $ ibmcloud cr namespace-add mephi42

    $ docker build -t registry.eu-gb.bluemix.net/mephi42/hello-wsk .
    $ docker push registry.eu-gb.bluemix.net/mephi42/hello-wsk

# Pitfalls
* Use `openwhisk/dockerskeleton` as a base or reverse engineer its entry point `/actionProxy/actionproxy.py`.
  `ibmcloud fn action create hello-world --docker hello-world` and the like will silently hang!
* If input JSON is small, it is passed via `argv[1]`, otherwise via `stdin`.
* The last `stdout` line must contain a JSON response. Other `stdout` lines, and all `stderr` lines are simply logged.
