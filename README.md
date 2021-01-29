# Base workflow image

The Docker image created by this workflow performs some very simple actions:

 * Starts from a vanilla Ubuntu 20.04 image.
 * Sets up a container user and group.
 * Includes the `fix-permissions` script to allow changing paths to be group owned.
 * Installs micromamba to allow child containers to install software with mamba.

Containers built on this image can be run as:

    docker run --user $(id -u):$(id -g) --group-add 100

such the container runs under the host UID, but giving this user access to all
the relavant parts of the container file-system.

