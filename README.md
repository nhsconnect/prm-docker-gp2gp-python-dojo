# prm-docker-gp2gp-python-dojo

A Dojo docker image with tools to build and test Python projects by GP2GP team.

Tested and released images are published to dockerhub as [nhsdev/gp2gp-python-dojo](https://hub.docker.com/r/nhsdev/gp2gp-python-dojo)

## Usage
1. Setup docker.
2. Install [Dojo](https://github.com/kudulab/dojo) binary.
3. Provide a Dojofile at the root of the project:
```
DOJO_DOCKER_IMAGE="nhsdev/gp2gp-python-dojo:<commit>"
```
4. Create and enter the container by running `dojo` at the root of project.

By default, current directory in docker container is `/dojo/work`.