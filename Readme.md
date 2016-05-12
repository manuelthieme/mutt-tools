# Mutt Tools

A collection of useful tools which I use in conjunction with my Mutt setu.

## mutt_profile

Since I use multiple Mutt instances for my different mail accounts, I created
a script which manages the configuration file hell for me. In addition to the
different accounts, I also start mutt in different modes. So for example for
normal reading or composing of mails. Accordingly, I have a relatively complex
directory structure to configure my Mutt, which looks as follows:

    mutt
     |-> mode1rc
     |-> mode2rc
     |-> account1
     |    |->     general
     |    |->     mailboxes
     |-> account2
     |    |->     general
     |    |->     mailboxes
     |    |->     mailinglists
     |-> common
          |->     general
          |->     colors
          |->     keybindings

The mode{1,2}rc files contain the mode depending settings and load additional files
from the common directory. In addition they also load account depending settings if
they require them.

The `mutt_profile` script selects and constructs the configuration files and then
starts Mutt with the correct settings.


## mutt_compose

I use this script to create additional terminal windows running their own mutt instance
to be able to write my mails in a different terminal than where I read my mails. The
script uses `mutt_profile` to spawn a new Mutt instance in the compose mode.


## mutt_view

This script is a small starter script which can be used to execute viewers for attachments
detached from the actual Mutt instance. The script will copy the file and then run the viewer
program in the background so that Mutt can be used as if nothing happened.


## mailboxsplit

I wrote this script to be able to extract all mailboxes belonging to one account from the
mailboxes file created by offlineimap. The script extracts the mailboxes and performs some
simple renaming so that Mutt properly understands them.


## mailmanage

`mailmanage` is a script which can automatically remove mails from a maildir which are older
than a specified number of days. I use this script to keep my maildirs which contain mails from
mailinglists small so that Mutt can open them as fast as possible.

The script is based on [mmanage](https://github.com/l3nkz/mmanage "mmanage"), a python tool designed
to perform archiving or cleaning operations on maildirs.
