# introduction
The container is running as user www-data with home directory /phive
To use phive in your project:
* build the container with correct user and group id flags
* add volume mounts to phive.xml and tools dir. For performance, also add /phive/.phive for loading cached phars

# usage
`docker run --rm -u $(id -u):$(id -g) -v /path/to/phive.xml:/phive/phive.xml -v /path/to/tools:/phive/tools -v /tmp/.phive:/phive/.phive phive install`
