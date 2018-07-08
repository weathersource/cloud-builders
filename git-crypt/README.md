# git-crypt

This build step provides a container with the git-crypt package
installed.

The entrypoint for this container is bash, so it is necessary to include the
whole make command.  For example:

steps:
- name: 'gcr.io/cloud-community-builders/make
  args: ['build']