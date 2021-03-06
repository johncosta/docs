:title: Using Multiple Accounts
:description: How to use multiple accounts on the dotCloud platform.
:keywords: dotCloud documentation, quick start guide, multiple dotCloud accounts, work environment

Using Multiple DotCloud Accounts
================================

If for some reason, you need to work with multiple DotCloud accounts,
you can use the DOTCLOUD_CONFIG_FILE environment variable to switch between
them.

To create a new DotCloud "work environment", you should set the variable
and then run "dotcloud setup". Later, you won't have to rerun "dotcloud setup"
(setting the environment variable will be enough).

For instance, to setup two accounts (a personal and a company account),
you can do like this::

  $ export DOTCLOUD_CONFIG_FILE=personal.conf
  $ dotcloud setup # enter your personal API key
  $ export DOTCLOUD_CONFIG_FILE=company.conf
  $ dotcloud setup # enter your company API key

Now, when you need to operate on an account, set the environment variable
beforehand::

  $ export DOTCLOUD_CONFIG_FILE=personal.conf
  $ dotcloud list # see your personal projects
  $ export DOTCLOUD_CONFIG_FILE=company.conf
  $ dotcloud list # see your company's projects

Remember: environment variables are local to a terminal or shell process.
If you open two terminal windows, and set the environment variable in the
first one, it won't affect the other window.

If you have to switch between accounts on a regular basis, you can use one
of the following tricks:

* setup shell aliases in your profile, bashrc or equivalent shell configuration
  file, so that running e.g. "dc-use-personal" and "dc-use-company" will set the
  relevant variables;
* use wrappers to set the environment variables for you just before running
  the actual dotcloud command, so that you can use e.g. "dotcloud-personal list"
  and "dotcloud-company push";
* if you are using Python, virtualenvs, and virtualenvwrapper, put the
  environment variable setting in the postactivate hook, so that when you
  "workon someproject" the DOTCLOUD_CONFIG_FILE variable is set as well.
