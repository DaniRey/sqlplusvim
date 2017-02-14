# sqlplusvim
 sqlplus.vim : Execute SQL queries and commands from within VIM (using Oracle's SQL*Plus) 

#created by
Jamis Buck
Dani Rey
 
#script type
utility
 
#description
This file contains routines that may be used to execute SQL queries and describe
tables from within VIM.  It depends on SQL*Plus.  You must have $ORACLE_HOME
$ORACLE_SID set in your environment, although you can explicitly set the
database name to use with the :DB <db-name> command.

##In command mode:
  <F7>: execute the whole script without applying any changes to it
  <F8>: execute the SELECT query under your cursor.  The query must begin with
        the "select" keyword and end with a ";"
  <Leader><F8>: prompt for an SQL command/query to execute.
  <F9>: treat the identifier under the cursor as a table name, and do a 'describe'
        on it.
  <F10>: prompt for a table to describe.
  <Leader>sb: open an empty buffer in a new window to enter SQL commands in
  <Leader>ss: execute the (one-line) query on the current line
  <Leader>se: execute the query under the cursor (as <F8>)
  <Leader>st: describe the table under the cursor (as <F9>)
  <Leader>sc: open the user's common SQL buffer (g:sqlplus_common_buffer) in a
              new window.

  :Select <...> -- execute the given Select query.
  :Update <...> -- execute the given Update command.
  :Delete <...> -- execute the given Delete command
  :DB <db-name> -- set the database name to <db-name>
  :SQL <...> -- open a blank SQL buffer in a new window, or if a filename is
                specified, open the given file in a new window.

##In visual mode:
  <F8>: execute the selected query

If queries contain bind variables, you will be prompted to give a value for each
one.  if the value is a string, you must explicitly put quotes around it.  If the
query contains an INTO clause, it is removed before executing.

You will be prompted for your user-name, password and tnsname the first time you access
one of these functions during a session.  After that, your user-id and password
will be remembered until the session ends.

The results of the query/command are displayed in a separate window.

You can specify the values of the following global variables in your .vimrc
file, to alter the behavior of this plugin:

  g:sqlplus_userid -- the user-id to log in to the database as.  If this
      is specified, g:sqlplus_passwd must be given as well, which is the
      password to use.  Default: ""
  g:sqlplus_path -- the path the the SQL*Plus executable, including any
      command line options.  Default: $ORACLE_HOME . "/bin/sqlplus -s"
  g:sqlplus_common_commands -- any SQL*Plus commands that should be
      executed every time SQL*Plus is invoked.
      Default: "set pagesize 10000\nset wrap off\nset linesize 9999\n"
  g:sqlplus_common_buffer -- the name of a file that will contain
      common SQL queries and expressions, that may be opened via the
      <Leader>sc command.
  g:sqlplus_db -- the name of the database to connect to.  This variable
      may also be modified via the :DB command.

All the honor goes to Jamis Buck "http://www.vim.org/account/profile.php?user_id=261"; who wrote the  first version "http://www.vim.org/scripts/script.php?script_id=97"; of this script. Unfortunately I can not maintain his original script, so I had to fork it.
 
#install details
Copy the sqlplus.vim script to your $HOME/.vim/plugin directory to install it for your user or copy it into $VIM_INSTALLATION_PATH/plugin to install it for all users on this server.  Make sure you have set ORACLE_HOME in your environment, to point to the root of your oracle installation.  (ie, $ORACLE_HOME/bin should contain sqlplus).
 
