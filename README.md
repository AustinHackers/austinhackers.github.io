AHA! Website
==

This repo contains the new [website for the AHA
group](http://takeonme.org). This is
replacing the old (and nasty) website that was previously hosted at wikidot.

How to submit your speaker materials 
--

This is primarily taken from the [Metasploit
Pull-Request](https://github.com/rapid7/metasploit-framework/wiki/Setting-Up-a-Metasploit-Development-Environment#wiki-pull) documentation
from [@corelanc0der](https://github.com/corelanc0d3r), as well as styling from
[tbaggery](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html). 

The procedure outline is as follows:

1. Create new branch
2. Create/copy new speaker-notes markdown file
3. Test changes locally with
	 [rake](https://github.com/AustinHackers/austinhackers.github.io/blob/master/Rakefile) (requires
	 [jekyll](http://jekyllrb.com/) and components be installed).
4. Commit changes to local repo
5. Push local branch to origin
6. Create/submit pull request on github.com
7. Clean up

### Create new branch
First, create a new branch from your master branch:

```
Please use the format YYYY-MM-DD-yourhandle
git checkout master
git checkout -b 2013-09-26-mauvehead
```

### Create/copy new speaker-notes markdown file
Either copy an existing speaker-notes file from another meeting or use
the template found in templates/. If you choose to use the template,
please remove the "Date:" line before your final commit. This line is
only required to make jekyll run without errors while testing locally
with rake.

Create/copy the speaker-notes markdown file, ensuring to put it in the
proper meeting folder \_posts/YYYY-MM-DD/ that you spoke at.

### Test changes with rake
With jekyll installed locally (follow quick-start-instructions from
[jekyll](jekyllrb.com) website), from the main root of the repo, run
*rake* to start jekyll and watch the output of the server. Now you can
navigate to [localhost:4000](http://localhost:4000) to view your changes.

### Commit changes, push branch to origin
Once it's all done and tested, add the changes to your repo and push
the branch up to origin:

```
git add <path to new speaker-notes>
git commit -m "added speaker-notes for mauvehead at meeting 2013-09-26"
git push origin 2013-09-26-mauvehead
```

Please make sure your commit messages conform to [this guide]
(http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).
TL;DR - First line should be 50 characters or less, then a blank line,
then more explanatory text if necessary, with lines no longer than 72
characters.

### Create/submit pull-request on github.com
This will automatically reference upstream's master as the branch to
land your pull request, and give you an opportunity to talk about how
great your module is, what it does, how to test it, etc.

Once you click Send Pull Request, you'll be on upstream's pull queue

### Wait for your pull-request to land
Now you must wait to the pull-request to be reviewed and landed by
someone with commit access. Your pull-request will be reviewed to verify
it matches requirements and compatibility.

This process has no real time line and could take days or longer. If
there is no movement on the pull-request ticket, you can always poke us
on IRC, or buy is booze.

### Clean up
Once your pull-request has landed upstream, you can clean up your local
branch after rebasing.

You can clean out your development branches with the following:

```
git branch -D 2013-09-26-mauvehead
git push origin :2013-09-26-mauvehead
```

Note that Git branches are cheap (nearly free, in terms of disk space),
so this shouldn't happen too terribly often.

