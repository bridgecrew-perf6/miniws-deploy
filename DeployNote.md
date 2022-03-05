# Steps to deploy mini-ws in kubernet cluster
- We have to change version of container image in deployment.yaml
## Organize deployment repo
- Should have deployment.yaml file
    - That should be a template with image container is placeholder to be filled with new version of code every time there is a merge in master
## Flow from new version to deployment
- New version merged in master -> generate new tag with this version
- Trigger deployment job (could be dedicated job in deployment repo)
    - deployment job clones repo + checkout latest tag (or tag given as input)
    - docker build with Dockerfile to generate image **in local** , name of docker image should follow a **convention**, so that the name is usable in deployment.yaml file in the next step
    - update name of image in deployment.yaml with new version image
    - `kubectl apply -f myws.deployment.yaml`
