# pm2 - My learning note - Learn or Die

Source: Notes
Status: Unprocessed
URL: https://tn710617.github.io/pm2/

![https://i.imgur.com/WIv3pVR.png](https://i.imgur.com/WIv3pVR.png)

---

## Introduction

### What’s pm2?

- pm2 is a process manager of Node.js

### What does pm2 solve?

- pm2 can re-launch Node service after it crashes.
- pm2 can re-launch Node service after the server reboot
- pm2 can run multiple processes with multiple cores of CPU to achieve Load Balancer like effect.
    - It features kind of rolling update, 0 downtime upgrade with Graceful Reload
    - Multiple services with multiple processes, significantly boost the performance.
    - Schedule to restart periodically
- pm2 provides much information, including restart number, CPU usage, memory usage, process id, etc.
- pm2 allows auto-restart under specific condition, such as ‘up-time’, ‘memory usage’, etc.
- pm2 can organise log, periodically split the log and keep the number we specify, delete exceeded ones.
- pm2 provides simple deployment method, and support multiple server deployment
- pm2 can integrate with CI / CD tool, as well as CI / CD deployment

`What are you waiting for?`

### Here are the coverage of this article:

- Installation
- pm2 with CLI
- pm2 with ecosystem
- pm2 with ecosystem on deployment
- pm2 deployment with GitLab CI / CD Runner

## installation

- Global installation

## pm2 with CLI

### Launch node project with pm2 with CLI, see the example below:

```
pm2 start location/fileName.js --name appName \--watch true \--max-memory-restart 500M \--log ~/.pm2/logs/appName/ \--time true \--cron "0 17 * * *" \--no-daemon true \--merge-logs
```

As to the meaning of CLI mentioned above, refer to the followings

### The flag

- `-name`Specify an app name
- `-watch`Watch and Restart app when files change
- `-max-memory-restart`Set memory threshold for app reload
- `-log`Specify log file
- `-output`specify out log file
- `-error`specify error log file
- `-log-date-format`prefix logs with custom formated timestamp
- `-merge-logs`when running mutiple process with same app name, do not split file by id
- `-arg1` `-arg2` `-arg3`Pass extra arguments to the script
- `-restart-delay`Delay between automatic restarts
- `-time`Prefix logs with time
- `-no-autorestart`Do not auto restart app
- `-cron`Specify cron for forced restart
- `-no-daemon`Attach to application log
    
    ## cluster mode
    
- pm2 automatically detect the number of CPU, launching as many processes as possible. The above mentioned flags could be attached on cluster mode. Specify how many process you would like after `i`. pm2 would automatically detect max number if you put `0` or `max`
    
    ## Process management
    
- Kill the process directly and restart a new process
- If it’s cluster mode, `reload` would reload process one by one and always keep one alive to achieve 0 downtime upgrade
- Stop and delete the app
- except for specifying app_name, you could also:`all` : all the Apps`id` : the id of the process
    
    ## Show the status of management
    

![pm2%20-%20My%20learning%20note%20-%20Learn%20or%20Die%20753414f7b61347d4a5e323ec7b06c553/WIv3pVR.png](pm2%20-%20My%20learning%20note%20-%20Learn%20or%20Die%20753414f7b61347d4a5e323ec7b06c553/WIv3pVR.png)

## Logs

- specify filepath to output both out and error logs
- Display X lines of api log file
- Output logs in json format
- Cancel logsBy specifying log path to `dev/null`, you could cancel log

## Rotated Log

If you’ve ever seen a single extremely big file with years of log, or you’ve ever found thousands of log files in a log folder, or you’ve ever come across weird log file naming, or you found a considerably huge amount consumed after you type `du -sh` in a folder, congratulations! Here is the solution.

### Installation

### Find the config file at `/home/user/.pm2/module_conf.json`

### Parameters

- max_size (Defaults to 10M):When a file size becomes higher than this value it will rotate it (its possible that the worker check the file after it actually pass the limit) . You can specify the unit at then end: 10G, 10M, 10K
- retain (Defaults to 30 file logs):This number is the number of rotated logs that are keep at any one time, it means that if you have retain = 7 you will have at most 7 rotated logs and your current one.
- compress (Defaults to false):Enable compression via gzip for all rotated logs
- dateFormat (Defaults to YYYY-MM-DD_HH-mm-ss) :Format of the data used the name the file of log
- rotateModule (Defaults to true) :Rotate the log of pm2’s module like other apps
- workerInterval (Defaults to 30 in secs) :You can control at which interval the worker is checking the log’s size (minimum is 1)
- rotateInterval (Defaults to 0 0 * * * everyday at midnight):This cron is used to a force rotate when executed. We are using node-schedule to schedule cron, so all valid cron for node-schedule is valid cron for this option. Cron style :
- TZ (Defaults to system time):This is the standard tz database timezone used to offset the log file saved. For instance, a value of Etc/GMT-1, with an hourly log, will save a file at hour 14 GMT with hour 13 GMT-1 in the log name.

### Graph

```
*    *    *    *    *    *┬    ┬    ┬    ┬    ┬    ┬│    │    │    │    │    |│    │    │    │    │    └ day of week (0 - 7) (0 or 7 is Sun)│    │    │    │    └───── month (1 - 12)│    │    │    └────────── day of month (1 - 31)│    │    └─────────────── hour (0 - 23)│    └──────────────────── minute (0 - 59)└───────────────────────── second (0 - 59, OPTIONAL)
```

## Terminal Based Dashboard

## pm2 ecosystem

CLI tool is good though, typo is so difficult to be eliminated. We could easily solve this problem by carefully crafting our ecosystem file. Except that some configs are meant to be changed in the future, we could eliminate typo issue. Besides, ecosystem cloud be controlled by Version Control System, like Git.

### Generate ecosystem file

### CLI

Same as above mentioned.

### Start specific App via ecosystem file

We could start specific App that we’d crafted in the ecosystem.config.js file.

### Parameter injection

Take a look on the following example. If I key in `pm2 start ecosystem --only app1 --env production`, then pm2 wil use the environment within env_production object.

### Parameter example

You could find tons of parameters below. Surely we are not going to use all of them, you could take a look on each of them and only leave those you need.

```
module.exports = {    apps: [        // First application        {            // application name (default to script filename without extension)            name: 'app1',            // script path relative to pm2 start            script: './server.js',            // the directory from which your app will be launched            cwd: 'var/www/yourApp/',            // mode to start your app, can be “cluster” or “fork”, default fork            exec_mode: 'cluster',            // number of app instance to be launched            instances: 0,            // enable watch & restart feature, if a file change in the folder or subfolder, your app will get reloaded            watch: false,            // your app will be restarted if it exceeds the amount of memory specified. human-friendly format : it can be “10M”, “100K”, “2G” and so on…            max_memory_restart: '500M',            // interpreter absolute path (default to node)            interpreter: '/root/.nvm/versions/node/v8.16.0/bin/node',            // option to pass to the interpreter            interpreter_args: "port=3001 sitename='first pm2 app'",            // alias to interpreter_args            node_args: "port=3001 sitename='first pm2 app'",            // Specify cron for forced restart            cron_restart: "0 17 * * *",            // Prefix logs with time            time: true,            // string containing all arguments passed via CLI to script            args: '-a 13 -b 12',            // list of regex to ignore some file or folder names by the watch feature            // Format could be array like "args": ["--toto=heya coco", "-d", "1"], or string like "args": "--to='heya coco' -d 1"            ignore_watch: ["[\/\\]\./", "node_modules"],            // default to true, [enable/disable source map file]            // http://pm2.keymetrics.io/docs/usage/source-map-support/            // https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/            source_map_support: true,            // instance_var, see documentation            // http://pm2.keymetrics.io/docs/usage/environment/#specific-environment-variables            instance_var: 'NODE_APP_INSTANCE',            // log date format (see log section)            log_date_format: 'YYYY-MM-DD HH:mm Z',            // error file path (default to $HOME/.pm2/logs/XXXerr.log)            error_file: '/var/log',            // output file path (default to $HOME/.pm2/logs/XXXout.log)            out_file: '/var/log',            // if set to true, avoid to suffix logs file with the process id            combine_logs: true,            // alias to combine_logs            merge_logs: true,            // pid file path (default to $HOME/.pm2/pid/app-pm_id.pid)            pid_file: 'user/.pm2/pid/app-pm_id.pid',            // min uptime of the app to be considered started            // format could be number 或 string. In number, 3000 means 3000 ms. If it's string, '1h' means 1 hour, '5m' means 5 minutes, '10s' means 10 seconds            min_uptime: '5',            // time in ms before forcing a reload if app not listening            listen_timeout: 8000,            // time in milliseconds before sending a final SIGKILL            // Refer to official documentation http://pm2.keymetrics.io/docs/usage/signals-clean-restart/            kill_timeout: 1600,            // Instead of reload waiting for listen event, wait for process.send(‘ready’)            // Refer to documentation http://pm2.keymetrics.io/docs/usage/signals-clean-restart/            wait_ready: false,            // number of consecutive unstable restarts (less than 1sec interval or custom time via min_uptime) before your app is considered errored and stop being restarted            // Refer to documentation http://pm2.keymetrics.io/docs/usage/signals-clean-restart/            max_restarts: 10,            // time to wait before restarting a crashed app (in milliseconds). defaults to 0.            restart_delay: 4000,            // true by default. if false, PM2 will not restart your app if it crashes or ends peacefully            autorestart: true,            // true by default. if false, PM2 will start without vizion features (versioning control metadatas)            vizion: true,            // a list of commands which will be executed after you perform a Pull/Upgrade operation from Keymetrics dashboard            post_update: ["npm install", "echo launching the app"],            // defaults to false. if true, you can start the same script several times which is usually not allowed by PM2            force: false,            // If no environment parameters are passed in, the default env will be within `env` object            env: {                COMMON_VARIABLE: 'true',                NODE_ENV: '',                ID: '44'            },            // If env is specified, env parameter will be within `env_specifiedEnvironment` object, for example, pm2 start ecosystem.js --env production            env_production: {                NODE_ENV: 'production',                ID: '55'            },            // Same as above            env_development: {                NODE_ENV: 'development'            }        },        // Second app, those mentioned above will not be repeated below        {            name: 'app2',            script: 'server.js',            // Default mode, and it supports other languages as opposed to cluster mode.            exec_mode: 'fork',            instances: 0,            watch: false,            max_memory_restart: '500M',            interpreter: '/root/.nvm/versions/node/v8.16.0/bin/node',            time: true,            env: {                COMMON_VARIABLE: 'true',                NODE_ENV: ''            },            env_staging: {                NODE_ENV: 'staging'            },            env_test: {                NODE_ENV: 'test'            }        }    ],    // Deployment section    deploy: {        // production        production: {            // SSH user            user: 'root',            // SSH host            host: ['host1', 'host2'],            // SSH key path            key: 'path/to/some.pem',            // GIT remote/branch            ref: 'origin/master',            // GIT remote            repo: 'git@gitlab.com:user/yourProject.git',            // path in the server            path: '/var/www/yourProjectName',            // Can be used to give options in the format used in the             // configuration file.             // This is useful for specifying options for which there             // is no separate command-line flag, see 'man ssh' can be            // either a single string or an array of strings            "ssh_options": "StrictHostKeyChecking=no",            // 在 pm2 要從 local 端連到 remote 端之前要執行的指令，可以多個指令，由 ; 分割，也可以指定 shell script 的檔案路徑            "pre-setup": 'apt update -y; apt install git -y',            // To prepare the host by installing required software (eg: git)            // even before the setup process starts            // can be multiple commands separated by the character ";"            // or path to a script on your local machine            "post-setup": "ls -la",            // Commands to execute locally (on the same machine you deploy things)            // Can be multiple commands separated by the character ";"            "pre-deploy-local" : "echo 'This is a local executed command'",            // Commands to be executed on the server after the repo has been cloned            'post-deploy': 'sudo /root/.nvm/versions/node/v8.16.0/bin/npm install && sudo /root/.nvm/versions/node/v8.16.0/bin/npm rebuild && /root/.nvm/versions/node/v8.16.0/bin/pm2 reload ecosystem.config.js',            // Environment variables that must be injected in all applications on this env            env_production: {                 NODE_ENV: 'production'            }        },         staging: {            user: 'root',            host: ['host3', 'host4'],            ref: 'origin/staging',            repo: 'git@gitlab.com:user/yourProject.git',            path: '/var/www/yourProjectName',            "ssh_options": "StrictHostKeyChecking=no",            "pre-setup": 'apt update -y; apt install git -y',            "post-setup": "ls -la",            "pre-deploy-local" : "echo 'This is a local executed command'",            'post-deploy': 'sudo /root/.nvm/versions/node/v8.16.0/bin/npm install && sudo /root/.nvm/versions/node/v8.16.0/bin/npm rebuild && /root/.nvm/versions/node/v8.16.0/bin/pm2 reload ecosystem.config.js',            env_production: {                 NODE_ENV: 'staging'            }        },    },};
```

## pm2 Deployment

pm2 Deployment supports multiple server deployment, also, which could integrate with CI / CD tool, automatically deploy after submitting a commit.

### Prerequisite

- Firstly, have you prepared the ssh key for local to remote? `The connection between local and remote is required.` Simply speaking, you need to put a private key locally, and put public key remotely. You could Google how to set up ssh key.
- Secondly, since pm2 will ssh to remote server, and then clone our project from either GitHub or Gitlab. So make sure that `cloning from Git Repository to remote server is feasible.` You will need to put a private key on your remote server, and the public key on Git Repository. Please also Google how to set up the key on GitHub or GitLab
- Since the first time we connect to remote server, ssh would prompt to ask if it’s okay to put the public key of remote server to local known host, we will need to config it in advance. Otherwise, the deployment would fail. We could cancel the hostKeyChecking feature.
- And then, we need to properly craft ecosystem file, let’s refer to the deploy example above.
- Finally, make sure ssh tunnel is not blocked (default port 22)

### Initialise remote folder

Before deploying, we need to set up the project on remote server. We could pass different parameters and pm2 would deploy accordingly.

### Deploy

- DeployAfter initially setting up our project on remote server, we could start to deploy.
- Here I’ve listed some parameters as follows, and you could also check details by `pm2 deploy help`

```
pm2 deploy <configuration_file> <environment> <command>  Commands:    setup                run remote setup commands    update               update deploy to the latest release    revert [n]           revert to [n]th last deployment or 1    curr[ent]            output current release commit    prev[ious]           output previous release commit    exec|run <cmd>       execute the given <cmd>    list                 list previous deploy commits    [ref]                deploy to [ref], the "ref" setting, or latest tag
```

- Relative commands of Deployment
- Force deploymentThat means that you have changes in your local system that aren’t pushed inside your git repository, and since the deploy script get the update via git pull they will not be on your server. If you want to deploy without pushing any data, you can append the –force option:

## CI / CD Deployment

- Implement deployment by integrating pm2 with GitLab CI / CD Runner, and here is the gitlab.yml example below:

```
# Use small-size imageimage: keymetrics/pm2:latest-alpinestages:- deployDeploy:  stage: deploy  script:  # If ssh-agent hasn't been installed, install it.  - 'which ssh-agent || ( apk add --update openssh )'  # Install bash for pm2 CLI  - apk add --update bash  # Install Git for connecting to remote server with pm2  - apk add --update git  # Implement ssh agent  - eval $(ssh-agent -s)  # Add ssh key to ssh agent. You could config the public key as GitLab's variable.  - echo "$SSH_PRIVATE_KEY" | ssh-add -  # Execute pm2 CLI  - pm2 deploy ecosystem.config.js production update  only:  - master
```

- If you set it properly, a simple git push would trigger the CI / CD deployment

## Auto start after reboot

- Generate startup script
- Cancel startup script
- 如果有更新 node 的版本，記得更新 script
- If you upgrade your node, udpate your script as well

## Reload after when content changes

Monitor files under the project folder and subfolder, and ignore `node_module`

```
cd /path/to/my/apppm2 start env.js --watch --ignore-watch="node_modules"
```

## update pm2

## pm2 cheat sheet

```
# Fork modepm2 start app.js --name my-api # Name process# Cluster modepm2 start app.js -i 0        # Will start maximum processes with LB depending on available CPUspm2 start app.js -i max      # Same as above, but deprecated.pm2 scale app +3             # Scales `app` up by 3 workerspm2 scale app 2              # Scales `app` up or down to 2 workers total# Listingpm2 list               # Display all processes statuspm2 jlist              # Print process list in raw JSONpm2 prettylist         # Print process list in beautified JSONpm2 describe 0         # Display all informations about a specific processpm2 monit              # Monitor all processes# Logspm2 logs [--raw]       # Display all processes logs in streamingpm2 flush              # Empty all log filespm2 reloadLogs         # Reload all logs# Actionspm2 stop all           # Stop all processespm2 restart all        # Restart all processespm2 reload all         # Will 0s downtime reload (for NETWORKED apps)pm2 stop 0             # Stop specific process idpm2 restart 0          # Restart specific process idpm2 delete 0           # Will remove process from pm2 listpm2 delete all         # Will remove all processes from pm2 list# Miscpm2 reset <process>    # Reset meta data (restarted time...)pm2 updatePM2          # Update in memory pm2pm2 ping               # Ensure pm2 daemon has been launchedpm2 sendSignal SIGUSR2 my-app # Send system signal to scriptpm2 start app.js --no-daemon # Do not run in the backgroundpm2 start app.js --no-vizion # By default, as well as ssh key is okay, pm2 would compare local and remote when restarting, and automatically pull the latest.pm2 start app.js --no-autorestart # Do not auto restart
```

## Auto completion

- pm2 command support auto completion

## 疑難雜症