## Creating a new site umbrella repository using this repository

This continues from https://gist.github.com/benlk/e4f555eb817940b817354f598408e57c

Using `sitename.org` as an example, and providing full pathnames in front of command-line prompts to help keep you located:

1. When running `vv create`, make notes of the answers you provide to the script.
2. From the directory above the wordpress installation, run `ls`. You should see something that looks like this:

	```
	/vagrant-local/www/sitename-org$ ls
	htdocs/      vvv-hosts    vvv-init.sh  wp-cli.yml
	```
3. Clone this repository to someplace safe:

	```
	/vagrant-local/www/sitename-org$ git clone git@github.com:INN/umbrella-boilerplate.git /tmp/umbrella-boilerplate
	```
4. Copy this repository's contents to your new site:

	```
	/vagrant-local/www/sitename-org$ rsync -rv --exclude=.git /tmp/umbrella-boilerplate/ htdocs/
	```
5. Make sure that the contents were copied by comparing the new install and the umbrella repo's contents

	```
	/vagrant-local/www/sitename-org$ ls /tmp/umbrella-boilerplate
	/vagrant-local/www/sitename-org$ ls htdocs/
	```
6. Now, initialize the submodules and do some other things

	```
	/vagrant-local/www/sitename-org$ ./initialize.sh
	/vagrant-local/www/sitename-org$ git status
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

	    modified:   .gitmodules
	    new file:   tools
	    new file:   wp-content/themes/largo

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

	    initialize.sh
	```

7. Clean up stuff from the boilerplate repository that will no longer be needed in the actual umbrella:

	```
	/vagrant-local/www/sitename-org$ rm ./initialize.sh
	/vagrant-local/www/sitename-org$ rm docs/README.md
	```

8. Prepare to commit: use `git add` to add all relevant files.

9. Commit: `git commit`


This doesn't set any variables. This doesn't fill out any text. This just gets you the files.
