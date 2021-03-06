# Kirby - Git Commit And Push Content

This is a plugin for [Kirby](http://getkirby.com/) that Commits and Pushes Changes made via the Panel to your Git Repository.

## Usage 

Just keep using the Panel as you are used to and watch the commits appear in your git repository!

## Installation

### Create a new git repository for your content

Create a new git repository where you push your content to, name it `your-project_content`.

Init the content repo and push it

Remove the `content/` folder from your current git repository
```
git rm --cached -r content
git add -A
git commit -m "Move Content Folder to separate repository"
``` 

Add the `content/` folder to new git repository

```
cd content
git init
git remote add origin https://github.com/your-project/your-project_content.git
git add -A
git commit -m "Initial Content Commit"
git push origin master
```

### Download and configure the Plugin

#### git submodules
Go into your `site/plugins/` folder and  
```
git submodule add --name git-commit-and-push-content https://github.com/blankogmbh/kirby-git-commit-and-push-content.git site/plugins/git-commit-and-push-content
cd site/plugins/
git submodule update --init --recursive
```

#### Composer
If you [installed kirby via composer](https://forum.getkirby.com/t/kirby-2-4-with-composer/5664/3?u=pascalmh) open your projects composer.json and add 
`blankogmbh/kirby-git-commit-and-push-content` as a requirement and a custom path so it will be installed into the site/plugins-Folder

Thats what your composer.json will look like afterwards:
```
{
    "name": "your-company/your-project",
    "require": {
        "mnsami/composer-custom-directory-installer": "1.1.*",
        "getkirby/kirby": "^2.4",
        "getkirby/panel": "^2.4",
        "blankogmbh/kirby-git-commit-and-push-content": "1.*"
    },
    "extra": {
        "installer-paths": {
            "./kirby": ["getkirby/kirby"],
            "./kirby/toolkit": ["getkirby/toolkit"],
            "./panel": ["getkirby/panel"],
            "./site/plugins/git-commit-and-push-content": ["blankogmbh/kirby-git-commit-and-push-content"]
        }
    }
}
```



#### copy & paste
Put all the files into your `site/plugins/git-commit-and-push-content/` folder. If the `git-commit-and-push-content/` plugin folder doesn't exist then create it.

### Options

You can use the following [Options](http://getkirby.com/docs/advanced/options) - make use of kirbys [Multi-environment setup](http://getkirby.com/blog/multi-environment-setup).

(In case you need to use multiple git users on your environment - [Multiple SSH Keys settings for different github account](https://gist.github.com/jexchan/2351996))

If you do not want to Pull and/or Push on every change you can also call `yourdomain.com/gcapc/push` or `yourdomain.com/gcapc/pull` manually (or automated with e.g. a cronjob).

#### gcapc-branch
Type: `String`
Default value: `'master'`

branch name to be checked out

#### gcapc-pull
Type: `Boolean`
Default value: `false`
 
Pull remote changes first?

#### gcapc-commit
Type: `Boolean`
Default value: `false`
 
Commit your changes?

#### gcapc-push
Type: `Boolean`
Default value: `false`
 
Push your changes to remote?

#### gcapc-cron-hooks-enabled
Type: `Boolean`
Default value: `true`

Whether `yourdomain.com/gcapc/push` and `yourdomain.com/gcapc/pull` are enabled or not.

#### gcapc-panel-widget
Type: `Boolean`
Default value: `true`

Show or Hide the Panel widget. 

#### gcapc-gitBin
Type: `String`
Default value: `''`

Sets the location where git can be found 

[See Git.php](http://kbjr.github.io/Git.php/) `void Git::set_bin ( string $path )`

#### gcapc-windowsMode
Type: `Boolean`
Default value: `false`

[See Git.php](http://kbjr.github.io/Git.php/) `void Git::windows_mode ( void )`

## Author

Pascal 'Pascalmh' Küsgen <http://pascalmh.de>
