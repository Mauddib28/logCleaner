# logCleaner
Script for removing footprints from logs

## history - shell/terminal
There are multiple places that one needs to lookout for when attempting to clean their tracks for:
1. History of the current shell/terminal
2. Long term history in the `.bash_history` file (accumulative)
Note: A "heavy handed" way to leaning history is `cat /dev/null > ~/.bash_history &&  history -c && exit`

### Breakdown of 'history' command
The more important points of the `history` command are as follows:
* `history` will print out the history of commands in the format of "\<command number\>	\<command\>"
