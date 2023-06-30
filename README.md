<!--
 Copyright (c) 2023 Anthony Mugendi
 
 This software is released under the MIT License.
 https://opensource.org/licenses/MIT
-->

# PM2 Deploy with ease!

If you have used **PM2 Deployment System** then you must know how powerful it is.

However, it can also get cumbersome when you have to enter the "Production server password" a million times!

These set of scripts simplify that process for you.

## Requirements

You will need to install [expect](https://linux.die.net/man/1/expect) and of course [PM2](https://pm2.keymetrics.io/)


## Installation  (Linux)

Simply clone this repo then add the `./bin` directory to your path.

```bash
# Clone
git clone https://github.com/mugendi/pm2-deploy.git
# make ./bin/pm2-deploy executable
chmod +x ./pm2-deploy/bin/pm2-deploy
# Edit .bashrc
nano ~/.bashrc
# Add this line to your file
export PATH="/your/path/pm2-deploy/bin:$PATH"
# Then reload .bashrc
. ~/.bashrc
```

Now go to your project and create a **Deployment Configuration** file as detailed [here](https://pm2.keymetrics.io/docs/usage/deployment/) and [here](https://pm2.io/docs/runtime/guide/easy-deploy-with-ssh/).

While in the project folder where your `ecosystem.config.js` is saved, run `pm2-deploy`

## So what does the script do?

This simple script asks for your server password at the beginning. It then uses [expect](https://linux.die.net/man/1/expect) to automatically fill in the passwords each time it is needed.

## But why not do it manually?

1. It is tedious
2. I wrote this script to automate things at the office. But to also ensure that employees can orchestrate deployments without needing to access or even know the production server passwords. All I/or someone else authorized is enter the password once and that's it. 

## Gotchas!

This script does not has a `--force` flag like you would do with `pm2 deploy production --force` to avoid breaking tour production server. Also it is expected that you will have **pre-commit hooks** to do all the necessary linting and testing. Therefore by the time you run this script you have committed and pushed your changes!

