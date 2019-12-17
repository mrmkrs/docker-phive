<img src="https://img.shields.io/docker/pulls/marcel0000/phive"> <img src="https://img.shields.io/docker/automated/marcel0000/phive">

# Introduction
This repository allows you to use phive in a docker image.
To use phive, add volume mounts to the following paths:
* /phive/phive.xml 
* /phive/tools

See https://hub.docker.com/r/marcel0000/phive

## Example
`docker run --rm -u $(id -u):$(id -g) -v /path/to/phive.xml:/phive/phive.xml -v /path/to/tools:/phive/tools -v marcel0000/phive:latest phive install`

## Caching
To preseve downloaded phars accros CI builds, mount an additional folder and setup the HOME directory:
This example adds a mount to the hosts /tmp folder, and sets the HOME directory to /cache. Now phive will store the downloaded phars on the hosts filesystem
`docker run -v /tmp:/cache -e HOME=/cache marcel0000/phive:latest phive install`

# Integration with CI
For automated builds, you need to trust the gpg keys for all phars defined in your phive.xml.

Example for trusting phpunit:

`docker run marcel0000/phive:latest phive install --trust-gpg-keys 4AA394086372C20A`

The keys to accept are printed when running `phive install`, but you should double check them yourself :-)
