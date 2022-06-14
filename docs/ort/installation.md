# Installation

## Docker

ORT is easiest to use with Docker. To use ORT with Docker, Docker needs to be installed on the host.

We publish a pre-built Docker image of ORT on [Docker
Hub](https://hub.docker.com/repository/docker/doubleopen/ort).

To properly use ORT with Docker, some configuration files need to accessible inside the container.
The most essential of these is the ORT configuration directory (defaults to `~/.ort/config`). Many
package managers also have configuration files, which may set alternative addresses for package
managers, or credentials for accessing them. A good starting point for passing a lot of the required
configuration files is to mount the home directory of the user from the host machine to the
container and setting the correct user in the container. An example for this can be found from
[ORT's example docker run
script](https://github.com/oss-review-toolkit/ort/blob/main/scripts/docker_run.sh).

## Native

Native installation may sometimes be simpler to run, for example if the setup
of credentials and proxies is complicated. To use a native installation of ORT,
the needed package managers need to be installed on the host. More information
can be found from
<https://github.com/oss-review-toolkit/ort/#running-the-tools>.
