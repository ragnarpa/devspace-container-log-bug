# Container log streaming bug in Devspace 5.2

If your Kubernetes Deployment contains multiple containers started from images
defined in devspace.yaml then `devspace dev` starts to stream logs only from one of
the containers.

## Repro

1. Start local Kubernetes cluster on Docker for Mac
2. `devspace build -b --skip-push`
3. `devspace dev`
4. Observe the log stream
5. Make a change in `index.js` and save it
6. You should see updates in the log stream (step 3)
7. You only see updates from one of the containers started from the images defined in `devspace.yaml`

## Expected result

After a developer starts `devspace dev` then all the logs from different containers (even if they are in the same pod)
should be shown in the log stream.
