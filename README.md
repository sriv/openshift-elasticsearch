openshift-elasticsearch
==================

This is a DIY cartridge for setting up ElasticSearch (currently 0.90.7) on Openshift, behind an Nginx proxy with basic auth. It also sets up Elastic Head (admin UI).

###Getting Started

- Create an account with [Openshift](http://openshift.com/)
- Install [RHC client](https://www.openshift.com/developers/rhc-client-tools-install)

####Setup rhc
    rhc setup


####Setup a new Teamcity application
    rhc app create <instance> diy-0.1 --from-code=git://github.com/sriv/openshift-elasticsearch.git -e SEARCH_USERNAME=<username> -e SEARCH_PASSWORD=<password>

Here,
- `<instance>` is the name of the application that you'd like
- `<username>` and `<password>` are the credentials that you'd like to setup.

For example, say

`openshift namespace` = `foo`
`<instance>` = `bar`

The url then looks like `http://bar-foo.rhcloud.com`.

*Elastic Head* is available at `http://bar-foo.rhcloud.com/_plugin/head/`

###Authentication on NGinx

This cartridge sets up an Nginx instance, with elasticsearch bound as one upstream. It uses basic auth for this. The username and password are setup using `htpasswd`
