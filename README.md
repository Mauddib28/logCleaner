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
  * The `-c` flag can be used to "clear the history list by deleting all of the entries"
  * The `-w- flag can be used to "write the current history to the history file"
  * The `-d \<command number\>` flag can be used to "delete the history entry as position OFFSET"

### Techniques for history clearing and cleaning
The following are different ways that one can go about cleaning the history file:
1. Clear the entire command line history
  * Viuew the current history with `history`
  * Clear the current history with `history -c` OR write the cleared one to `.bash_history` using `history -cw`
2. Clear commands by using an inserted blank space before each command
  * Note: To get this to work, you must set the `HISTCONTROL` environment variable as `ignorespace` or `ignoreboth`.  Example: `export HISTCONTROL=ignorespace`
  * Now everytime a command is typed into the shell, then ANY command that has a space character at the start will be ignored from being added to the history file
3. Clear or delete specific commands from history
  * Use the `history -d \<command number\>` to remove specific commands from the history file
4. Clear command line history automatically when logging out
  * Edit the `.bashrc` file: `vi ~/.bashrc`
  * Add the following line: `unset HISTFILE`
5. Deleting the command line history perminantly
  * Note: To remove ALL commands from history of ALL terminal sessions, one must remove the contents of the `.bash_history` file
  1. To clear the contents manually one can: `cat /dev/null > ~/.bash_history`
  2. Can schedule the task via cron jobs
    * Run `crontab -e`
    * Add the following commands: `00 20 * * * cat /dev/null > ~/.bash_history`
    * Note: This will have the history be cleared everyday at 8pm
