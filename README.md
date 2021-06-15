# Rackspace Cloud Databases API documentation

[![Netlify Status](https://api.netlify.com/api/v1/badges/76a13343-5b17-4fb5-a2fc-a174d383c036/deploy-status)](https://app.netlify.com/sites/docs-cloud-databases/deploys)

This repository contains the source files that generate the following Cloud databases API documentation:

* [Getting started](https://developer.rackspace.com/docs/cloud-databases/v1/getting-started/)
* [General API information](https://developer.rackspace.com/docs/cloud-databases/v1/general-api-info/)
* [API reference](https://developer.rackspace.com/docs/cloud-databases/v1/api-reference/)
* [Release notes](https://developer.rackspace.com/docs/cloud-databases/v1/release-notes/)

When you commit changes to the master branch of this repository, the
[Strider CI/CD build job](https://build.developer.rackspace.com/rackerlabs/docs-cloud-databases/)
builds the documentation. Successful builds are deployed to production.

## Local Setup

`npm i -g netlify-cli`
`netlify init`
`netlify build`
`netlify dev`
`netlify deploy`

### Support and feedback

We welcome feedback, comments, and bug reports. Follow the
[contributor guidelines](https://github.com/rackerlabs/docs-cloud-databases/blob/master/CONTRIBUTING.md)
to propose a source file change, or [submit a GitHub issue](https://github.com/rackerlabs/docs-cloud-databases/issues/new)
to request an update or to provide feedback.

You can also contact the [Rackspace documentation team](mailto:devdoc@rackspace.com) directly for general issues
or questions about the content.
