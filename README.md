# Packer images

Packer is a free and open source tool for creating golden images for multiple platforms from a single source configuration.

## Pre-requisites

Before you can run packer to build images, you'll need the following pre-requisites:

* Packer
    * MacOS - `brew install packer`
    * Windows - `choco install packer`
* Access to the AWS account where the images will be built
* Administrator password for image

## Variables

The following environment variables should be set before running packer:

* AWS Credentials
    * `AWS_ACCESS_KEY_ID`
    * `AWS_SECRET_ACCESS_KEY`
    * `AWS_SESSION_TOKEN`
* Administrator Password
    * `PACKER_ADMIN_PASSWORD`

## Building Packer Image

Currently, this automation assumes that you'll be building resources in US-West-2 AWS region.

In order to build the windows AMI, set the environment variables as mentioned previously and run the following command from the root of the project:

`packer build <path to json file>`

It will take a little while for the image to be generated. Once the process is completed, you'll see the image under `Services -> EC2 -> AMIs`.

The AMI ID will be output at the end.
