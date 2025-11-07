# ptero-gh-actions-runner
Pterodactyl egg alongside with a custom ubuntu docker image to self-host Github Actions runnner

## How to configure a new runner

1. Ensure you have the most recent version of [Custom Ubuntu build](https://github.com/shmitzas/ptero-gh-actions-runner/custom_ubuntu_build)
2. Navigate to your Github repository's runners tab
    ```
    https://github.com/<gh username>/<gh repository>/settings/actions/runners/new
    ```
3. Take note of `URL` and `TOKEN` variables in configuration step
4. Import the `GH Actions Runner` json configuration to your pterodactyl panel
5. In your pterodactyl panel create a new server and input these variables to the starup configuration fields
6. Start up you container
7. After container installs, launch it and input the start command manually (doesn't work when automated, fuck knows why x_x)
    ```bash
    bash /home/container/actions-runner/run.sh
    ```
