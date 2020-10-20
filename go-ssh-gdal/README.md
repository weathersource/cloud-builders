This builder creates a debian docker image - which playes nicer with the GDAL libraries than the alpine images do.

# Go Builder

To build a new 'gcr.io/example-project/go-ssh-gdal' image:

    cd path/to/cloud-builders/go-ssh-gdal 
    gcloud config set project wx-microservices 
    gcloud builds submit --config=cloudbuild.yaml


### Pulling from private repositories

To pull from private repositories, follow the steps below:

```
# Set your SSL keys to the /root/.ssh volume. Follow the tutorial at
# https://cloud.google.com/container-builder/docs/access-private-github-repos

# force `go get` to use SSH instead of HTTPS for github repositories
- name: 'gcr.io/example-project/go'
  entrypoint: ash # for alpine, `bash` for debian
  args:
  - '-c'
  - |
    git config --global --add url."git@github.com:".insteadOf "https://github.com/"

# get go package dependencies using SSH
- name: 'gcr.io/example-project/go'
  args: ['get']
  env: ['PROJECT_ROOT=app']
  volumes:
  - name: 'ssh'
    path: /root/.ssh

# install the app
- name: 'gcr.io/example-project/go'
  args: ['install', '.']
  env: ['PROJECT_ROOT=app']

```
