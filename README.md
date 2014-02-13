# Chronos / Docker integration

Allows you to use docker containers in [Chronos](https://github.com/airbnb/chronos).

## Usage

When creating a new job in Chronos, we need to specify the command shown as below

When using WebGUI
```json
Generic:
    {"container" : "<NAME_OF_DOCKER_CONTAINER>", "cmd" : "<COMMAND_TO_RUN_IN_DOCKER>", "params" : "<ANY_ARG_SUPPORTED_BY_DOCKER>"}

Example:
    {"container" : "ubuntu", "cmd" : "/bin/bash", "params" : "-n -h='my_test_docker'"}
```

When using CLI
```json
Example:
    echo '{"schedule":"R/2014-02-14T00:52:00Z/PT90M", "name":"cli_docker_executor", "command": "{ \"container\" : \"docker_chronos_test\", \"cmd\": \"/root/docker_test.sh\"}", "epsilon":"PT15M", "executor":"/var/lib/mesos/executors/chronos_docker" }' | http POST localhost:8080/scheduler/iso8601
```
* NOTE: We need to escape quotes in command when using CLI.


#### Forked from
* https://github.com/mesosphere/mesos-docker


### Todo list

- Adding try / except for different checks