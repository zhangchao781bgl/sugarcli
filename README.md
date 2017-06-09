# SugarCli
SugarCli is a command line tool to install and manage SugarCRM installations.


# Installing
Get the latest phar archive at `https://getsugarcli.inetprocess.fr/sugarcli.phar`. Allow the execution and run it.
```
wget 'https://getsugarcli.inetprocess.fr/sugarcli.phar'
chmod +x ./sugarcli.phar
./sugarcli.phar
```

Or clone this git repository and use `./bin/sugarcli`.


# Building
Clone the git repository and run
```sh
composer install --no-dev --quiet -o
mkdir build
ulimit -Sn 4096
php -dphar.readonly=0 bin/box build
```
It will build the `sugarcli.phar`  Phar archive in the `build` folder.


# Configuration
You can save some configurations options in different location. The latter one will override the previous one:
`/etc/sugarclirc`
`$HOME/.sugarclirc`
`./.sugarclirc`

Command line parameters will override these configurations.

## Example
```yaml
---
sugarcrm:
    path: PATH          #Path to Sugarcrm relative to the configuration file
    user_id: USER_ID    #SugarCRM user id to impersonate when running the command
metadata:
    file: FILE          #Path to the metadata file relative to the configuration file
account:
    name: ACCOUNT_NAME  #Name of the account
```


# Usage
* `./sugarcli.phar list`: List all commands available
* `./sugarcli.phar namespace:command --help`: Display help for a specific command

See the [USAGE.md](USAGE.md) file for a complete list of commands and the associated help

# Development
## Run tests
Copy the file `phpunit.xml.dist` to `phpunit.xml` and edit the environment variables.

Run the full test suite with `bin/phpunit` or exclude groups to avoid required external resources `bin/phpunit --exclude-group inventory,sugarcrm-db`

__Available groups__:
* inventory
* sugarcrm-db
* sugarcrm-path
* sugarcrm-url

