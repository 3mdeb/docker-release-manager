# docker-release-manager

## Prerequisites

Each container repo managed by this script shall contain the `container-config`
file with content:

```
DOCKER_USER_NAME="user-name"
DOCKER_IMAGE_NAME="image-name"
```

and a `VERSION` file that follows the syntax:

```
X.Y.Z
```

To enable `Trevis CI` in a given repo, add a `.travis.yml` based on the [provided
example](travis.yml.example).

## Bump version

1. Enter container repo.

1. Call the bump script:

    ```
    curl -s https://raw.githubusercontent.com/3mdeb/docker-release-manager/master/release-manager.sh | bash /dev/stdin bump_minor
    ```

1. Create PR.

1. If Travis job triggers, wait for the build to pass. Then, merge the PR to `master`.

1. Builds from `master` are automatically being pushed to `dockerhub`.
