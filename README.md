# Packer images

Packer is a free and open source tool for creating golden images for multiple platforms from a single source configuration.

## Reference

* https://www.packer.io/docs/provisioners/ansible.html

## Pre-requisites

Before you can run packer to build images, you'll need the following pre-requisites:

* Packer
    * MacOS - `brew install packer`
    * Windows - `choco install packer`
* Access to the AWS account where the images will be built
* Administrator password for image
* Pyenv
* Pipenv
* [Windows Update Packer Provisioner](https://github.com/rgl/packer-provisioner-windows-update)

## Variables

The following environment variables should be set before running packer:

* AWS Credentials
    * `AWS_ACCESS_KEY_ID`
    * `AWS_SECRET_ACCESS_KEY`
    * `AWS_SESSION_TOKEN`
* AWS Environment
    * `AWS_VPC_NAME`
    * `AWS_SUBNET_NAME`
* Administrator Password
    * `PACKER_ADMIN_PASSWORD`
* Artifactory Credentials
    * `ARTIFACTORY_USERNAME` - your email address
    * `ARTIFACTORY_TOKEN` - your Artifactory API token
    * `ARTIFACTORY_URL` - URL of Artifactory server

For large AMI bulds, you may need to extend the timeout for the AMI image creation by setting the following environmental variables.

* `AWS_MAX_ATTEMPTS` - 60
* `AWS_POLL_DELAY_SECONDS` - 90

## Building Packer Image

Currently, this automation assumes that you'll be building resources in US-West-2 AWS region.

Go into the Pipenv Shell

`pipenv shell`

Set the environment variables

In order to build the windows AMI, set the environment variables as mentioned previously and run the following command from the root of the project:

`packer build <path to json file>`

It will take a little while for the image to be generated. Once the process is completed, you'll see the image under `Services -> EC2 -> AMIs`.

The AMI ID will be output at the end.
