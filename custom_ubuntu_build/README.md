# Customized Ubuntu build

This build includes all needed packages and directory configuration for self-hosting Github Actions runners.

## How to compile and publish the build

If you need to modify something, make sure to re-build and re-publish the image before trying to use it,

1. Authenticate to Github Container Registry
   1. Create your general (classic) PAT with `write:pakcage` permissions
   2. Authenticate to ghcr.io using your GH account
        ```bash
        docker login ghcr.io -u shmitzas
        ```
2. Build the image
    ```bash
    docker build -f Dockerfile.runner-base -t ghcr.io/<gh username>/gh-actions-runner-base:22.04 .
    ```
3. Publish the build
     ```bash
     docker push ghcr.io/<gh username>/gh-actions-runner-base:22.04
     ```

## How to make sure your pterodactyl panel can use this image

1. SSH to your pterodactyl host VM
2. Navigate to `/etc/pterodactyl`
3. Open `config.yml`
4. Find `docker` section
5. Add your Github Container Registry credentials
    ```yaml
    registries:
    ghcr.io:
      username: <gh username>
      password: <gh PAT>
    ```
6. Save `config.yml`
7. Run `systemctl restart pteroq.service` to apply the changes
    