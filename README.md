* Create an account on [fly.io](fly.io) if you don't have one.
* Edit the `fly.toml` files in the root and in docker-daemon and replace the instances of `<app_name>` to be the name you want.
* Run `fly launch --no-deploy` in the root dir and accept the fly.toml config that is already there
* Set up the volume `fly volumes create gitea_data -s 10`, replace 10 with however many GB you want the volume to be. It can be expaned later.
* Run `fly deploy`
* Go to your new app and set up your gitea account
* On admin settings > actions > runners get your runner token from the `create new runner` button
* Go to the `.dockercmd` file and replace `<token>` with the token you copied
* `cd docker-daemon`
* `fly launch --no-deploy` and create another volume `fly volumes create <app_name>_data -s 10`
* `fly ssh console` and run the `docker run` command from the `.dockercmd` file to start your runner

Congrats. You now have a gitea instance that can run gitea actions.

For more setup go to [renovate_config](https://github.com/letto4135/renovate_config) and clone it into your gitea instance to run a dependabot like job.

Once this is set up you can also clone this repo into your gitea instance and it will deploy itself when changes are made to configs.
