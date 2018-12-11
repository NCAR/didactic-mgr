# DIDACTIC-MGR - DIDACTIC Management Github Repository

"Didactic" (Docker Image Deployment Automation with Controlled Tags In CircleCi)
is a script-based framework for deployment automation using CircleCI.
This GitHub repository tracks and triggers software deployments in NCAR/SWES's
CI/CD pipeline. Each deployable project/service has its own branches in the
repo; there is a branch for each project/environment combination. For example,
to manage staging and production deployments for a project called "NCAR/foo",
the repo would have branches called `NCAR/foo/staging` and `NCAR/foo/prod`.

The primary role of the repository is to trigger CircleCI builds to deploy
images. The deployment process starts when a metadata file that describes an
image is committed to a project/environment branch. This triggers a CircleCI
build against the `didactic-mgr` repo; in this build, the target of the
deployment is identified through the branch name, and the image to deploy
is identified through the metadata file. The build job then triggers a new
CircleCI build against the target project's repo; this new job deploys
the image.

To control who can deploy a given service to a given environment, GitHub's
"protected branch" feature can be used to define who can commit to the
relevant branch.

In addition to triggering builds, this repository is also responsible for
maintaining deployment logs for each project. The logs are maintained in the
`master` branch, and record when images are authorized for deployment and
when they are actually deployed.








