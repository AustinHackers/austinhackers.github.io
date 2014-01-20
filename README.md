AHA! Website
==

This repo contains the new [website for the AHA
group](http://takeonme.org). This is
replacing the old (and nasty) website that was previously hosted at wikidot.

How to submit your speaker materials
--
*(the easy pointy-clicky way)*


  * Fork https://github.com/AustinHackers/austinhackers.github.io . Now you're on your fork. Note, this step only happens once (keep your fork forever).
  * If you already have a fork, you first need to sync it to the AustinHackers master repo (see documentation below)
  * Navigate to `templates/speaker_notes.md`, click edit. Or, just visit: https://github.com/todb/austinhackers.github.io/edit/master/templates/speaker_notes.md
  * Copy that to your clipboard.
  * Navigate to the correct meeting. Eg: https://github.com/todb/austinhackers.github.io/tree/master/_posts/2013-11-21-0x0056
  * Create a new branch, named my-awesome-talk, by filling in the new name in the blue "Branches" box.
  * Click on the blue `[+]` button to create a new file. Requires JS/Flash. No direct nav.
  * Name your file YOURNAME.md. Note the directory name you're already in.
  * Paste your copied template.
  * Update your name and the meeting ID (the former you know, the latter you can learn by looking at the current directory name).
  * Write your thrilling summary using GitHub-flavored markdown.
  * Write a short commit summary (50 characters max please). This will not be shown on the website.
  * Write more description if you like. Again, just for the upcoming pull request and commit histories.
  * Hit the green Commit New File button.
  * Hit the grey Pull Request button.
  * Hit the "Click to create a pull request for this comparison" link if that looks good to you.
  * Click the green Send pull request button.
  * Annoy someone on #aha on Freenode to land it.

Upsides to this method:

  * All in-browser. No local clones required.
  * Hella easy when you do it more than once.

Downsides:

  * You cannot GPG-sign your changes. Boo.
  * You don't get the full set of git commands for branch and commit management. You won't miss them, though.
  * If your commit message is malformed, you won't notice. You have to count characters with your eyeballs.

Syncing to Upstream (using the github.com website):
  * From your forked repo in github.com, click the green button with the two white arrows that represents the compare & review function, right next to the drop down for your current branch
  * If you are behind it should show something like, "There isn't anything to compare, try switching the base for your comparison". Click that link.
  * You should now see all the changes in the upstream master that you must sync
  * Hit the "Click to create a pull request for this comparison" link if that looks good to you.
  * Towards the top of the page click the "Create pull request from these changes" link
  * Fill out any commit information you want (this will be logged in YOUR forked repo)
  * Click the green Send pull request button.

----

If you are more comfortable with the git command line interface, and want access to more complicated git functions not available via the GitHub UI, read on.

How to submit your speaker materials
--
*(the hard way)*


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
8. Resyncing from upstream

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
From your github page, navigate to your forked copy of the AHA! Website
repo. Find your new branch that you just created and pushed up to your
origin in the previous step. Look in the top right corner of the box
that shows your source code, is a link that says *Pull Request*. Click
this and continue on.

This will automatically reference upstream's master as the branch to
land your pull request.

Once you click Send Pull Request, you'll be on upstream's pull queue.

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

### Resyncing from upstream
The general idea here is to always use a new branch to create new
content you want to submit to the main AHA repo, known as upstream. In
doing so you'll never work directly from your *master* branch, you'll
instead use new branches for each feature or speaker note.

With this idea in mind, your *master* branch should always be an up to
date version of the upstream AHA repo.

The following will set this up:

1. Add remote upstream (do only once)
```
git remote add upstream git@github.com:AustinHackers/austinhackers.github.io.git
```

2. Verify it was added (optional)
```
git remote -v
```

3. Grab all remote objects
```
git fetch --all
```

4. Sync your local master with the latest from upstream
```
git reset --hard upstream/master
```

5. Push your local master to YOUR origin/github profile (optional)
```
git push origin master
```

