# Instructions

Create a similar deployment pipeline for a simple Node.js/Express app found here (opens in a new tab).

Either clone the project or copy the files to your own repository.

Set up a similar deployment pipeline, or the "first half", using GitHub Actions as described earlier. Ensure that a new image gets pushed to Docker Hub every time you push code to GitHub. For example, you can change the message the app shows.

```yaml
name: Release Node.js app

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # ...
```

Some of the actions that the example above uses may already be outdated, so go through the documentation and use the most recent versions in your workflow:

- `actions/checkout`
- `docker/login-action`
- `docker/build-push-action`
- `docker/setup-buildx-action`

Keep an eye on the GitHub Actions page to see that your workflow is working.

Ensure also from Docker Hub that your image gets pushed there.

Next, run your image locally in detached mode and ensure that you can access it in the browser.

If you use an M1/M2 Mac, the image built by GitHub Actions might cause problems on your machine due to different processor architecture. One way to get around this is to build a multi-platform image; see here (opens in a new tab) for more.

Now set up and run Watchtower just as described above.

Now your deployment pipeline is set up. Ensure that it works:

- Make a change to your code.
- Commit and push the changes to GitHub.
- Wait for some time (the time it takes for GitHub Actions to build and push the image plus the Watchtower poll interval).
- Reload the browser to ensure that Watchtower has started the new version and that your changes are visible.

Extend `docker-compose.yaml` to start up both Watchtower and the Express app.

As an answer, submit a link to the repository with the configurations.
