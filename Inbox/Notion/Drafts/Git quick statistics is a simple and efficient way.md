# Git quick statistics is a simple and efficient way to access various statistics in git repository.

Source: Website
Status: Unprocessed
URL: https://git-quick-stats.sh/

![Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364013-61e53800-7e7b-11e9-87f9-790d6744fbd5.png](Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364013-61e53800-7e7b-11e9-87f9-790d6744fbd5.png)

## Features

## More screenshots

![Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364011-61e53800-7e7b-11e9-9417-16cbb241ac2e.png](Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364011-61e53800-7e7b-11e9-9417-16cbb241ac2e.png)

![Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364010-61e53800-7e7b-11e9-8711-a40b50aebf52.png](Git%20quick%20statistics%20is%20a%20simple%20and%20efficient%20way%2003022809113f4d7b82b276b9343b6512/58364010-61e53800-7e7b-11e9-8711-a40b50aebf52.png)

## Getting started

- **Interactive usage**
    - git-quick-stats has a built-in interactive menu that can be executed as such:  `git-quick-stats`  Or  `git quick-stats`
- **Non-interactive usage**
    - For those who prefer to utilize command-line options, git-quick-stats also has a non-interactive mode supporting both short and long options:  `git-quick-stats [optional-command-to-execute-directly]`  Or  `git quick-stats [optional-command-to-execute-directly]`
    - Command-line arguments:  `r, --suggest-reviewers` show the best people to contact to review code `T, --detailed-git-stats` - give a detailed list of git stats `R, --git-stats-by-branch` see detailed list of git stats by branch `d, --commits-per-day` displays a list of commits per day `m, --commits-by-month` displays a list of commits per month `w, --commits-by-weekday` displays a list of commits per weekday `o, --commits-by-hour` displays a list of commits per hour `A, --commits-by-author-by-hour` displays a list of commits per hour by author `a, --commits-per-author` displays a list of commits per author `S, --my-daily-stats` see your current daily stats `C, --contributors` see a list of everyone who contributed to the repo `b, --branch-tree` show an ASCII graph of the git repo branch history `D, --branches-by-date` show branches by date `c, --changelogs` see changelogs `L, --changelogs-by-author` see changelogs by author `j, --json-output` save git log as a JSON formatted file to a specified area `h, -?, --help` display this help text in the terminal

## Documentation

- **Git log since and until**   `export _GIT_UNTIL="2017-01-22"`
    
    You can set the variables _GIT_SINCE and/or _GIT_UNTIL before running git-quick-stats to limit the git log.  These work similar to git's built-in --since and --until log options.
    
    Once set, run git quick-stats as normal. Note that this affects all stats that parse the git log history until unset.
    
- **Git log limit**
    
    You can set variable _GIT_LIMIT for limited output. It will affect the "changelogs" and "branch tree" options.
    
                                        `export _GIT_LIMIT=20`
                                    
    
- **Git pathspec**   `export _GIT_PATHSPEC=':!directory'`
    
    You can exclude a directory from the stats by using pathspec
    
    You can also exclude files from the stats. Note that it works with any alphanumeric, glob, or regex that git respects.
    
                                        `export _GIT_PATHSPEC=':!package-lock.json'`
                                    
    
- **Git merge view strategy**
    
    You can set the variable _GIT_MERGE_VIEW to enable merge commits to be part of the stats by setting _GIT_MERGE_VIEW to enable. You can also choose to only show merge commits by setting _GIT_MERGE_VIEW to exclusive. Default is to not show merge commits. These work similar to git's built-in --merges and --no-merges log options.
    
                                        `export _GIT_MERGE_VIEW="enable"
                                        export _GIT_MERGE_VIEW="exclusive"`
                                    
    
- **Color themes**
    
    You can change to the legacy color scheme by toggling the variable _MENU_THEME between default and legacy
    
                                        `export _MENU_THEME=legacy`
                                    
    

## Want to show your support? Donate via Bitcoin or buy me coffee

If you or your company use this project or like what We're doing, 
 please consider backing us so We can continue maintaining and evolving this project and new ones.

### **Why donate?**

Many people love this service and have asked to donate. If you want to kick in to help me cover those costs, that would be awesome!

### **Choose what you'd like to donate from the items below then click the button:**

The easiest way to support us financially is by buying or subscribing to one of our tiers. 
If you'd like to make a donation to keep us going, support us via Github Sponsors.

# Thank you for your support! 🙌

© 2017-2021. All rights reserved