# silence

"everything is so peaceful without all the gab" ;p

## installation

if you plan on using this script in admin mode (see below for explanation) you won't need to install anything as it uses
the gems that your mastodon installation uses. you *will* need bundler 2+, but you should already have that because you have
mastodon installed.

if you plan on using the script in user mode (see below for explanation) you'll need to clone (or download) this repo and run

`bundle install` 

in the folder, assuming you have ruby and bundler installed.

## usage

`./silence --help`

the script supports two modes: admin and user mode

### admin mode

admin mode is meant for server administrators as it creates server level blocks.

to run in admin mode, you'll need to pass the option `-a` and have the `RAILS_ENV` environment var set to 'production'

the script assumes the mastodon root folder is the parent folder (as in, this git repo is placed inside the mastodon root folder), however you can specify the relative path to the root folder by using the `-p` option

example usage: `./silence -a -p '../mastodon'`

example usage setting envvar: `RAILS_ENV=production ./silence -a -p '../mastodon'`

### user mode

user mode is meant for typical users and creates domain blocks for that user

this is the default mode for the script. on the first run you'll need to pass in an access token and an instance url

after this first time the script will save this information so you don't have to re-run with those extra options

if you don't know how to get a token, please read the next section

example first run usage: `./silence -i 'mastodon.social' -t 'CoOl_T0KEn'`

example post first run usage: `./silence`

## getting an access token

1. login to your mastodon account
2. go to settings
3. click the 'development' heading on the side
4. click the 'new application' button
5. you can put anything in for 'name' (scopes can stay the default but if you're privacy minded you can uncheck all scopes except `read:blocks` and `write:blocks`)
6. click the submit button at the bottom. this will take you back to the development menu
7. click the newly created application
8. highlight and copy the access token
9. you did it! use that token on the first run usage! :3


## unsolicited advice from me~

im just gonna add this script into my crontab, and i personally suggest you do too.

if you're using admin mode, it might be easier to add `RAILS_ENV=production` into your shell's initialization file,
that way you don't have to worry about adding it in for every invocation.

oh! and before you run this in user-mode make sure you're admin isn't already using it. it won't hurt anything, just a bit redundent :p
