# Troubleshooting IDE and other Technical Issues

This lesson won't cover all the issues that you'll encounter when working with students. For that, refere to [this document in the Reference Guide](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md). 


## Tracking issues

We want to make sure that we’re tracking all of the Learn IDE issues we see. This include things as small as "`ctrl+v` breaks the console and we have to reconnect", to "we had to `rm -rf` the lab and re-clone to get it to work", to "can not get the lab into the students IDE". Please include all resolved and unresolved issues so that the team here has as much data as possible to help make the IDE the best product it can be. Track all issues in this spread sheet (pinned in the #learn-expert channel on slack): https://docs.google.com/spreadsheets/d/1YE89PzBQCO4RHCce5WXZA2WRUmJmnZnt_7LxbFSO9Xk/edit#gid=0 . 

If the issue is something that's been seen many times before, we only need to fill in the three columns highlighted in red (Issue, OS, and Version). If the issue is new or more complex, please fill in all columns. If you have any questions, don't be afraid to ask!

Below are a list of common questions a student might have about the IDE/

## The IDE isn't working for me.

At the bottom right corner do you see a [green Learn](http://www.screencast.com/t/ynriNugHfC3)?

Or is there a [red DISCONNECTED](http://www.screencast.com/t/CTOlLehAz4J)? If it is disconnected tell the student to go to Packages-->Learn.co-->Reconnect.

##I see 'Not authorized.' in the terminal

This means the student entered their OAuth Token incorrectly. To fix, they should click on Atom > Open Your Config (Mac) or File > Open Your Config (Windows). Atom will open a file with lines that look something like this:

```
"integrated-learn-environment":
    oauthToken: "oauth_token_here"
```

The user should visit https://learn.co/ile/token, correctly paste it into this file, and then save. They will then need to quit the Learn IDE (using the Atom or File menu).

If the user does not already have the above code snippet in their config folder, just add those lines right under the `userId:...` bit.

## I see 'No passwd entry for user "username"'

This means one of two things:

1) The user's account was not created on the IDE server

or

2) The user has changed their GitHub username between when their account was created on the IDE server and when they tried to connect.

In the case of #2, please [provision](https://github.com/learn-co-curriculum/learn-expert-learn-ide-workflow) the students account. If that does not fix the issue, ping [#escalation](https://github.com/learn-co-curriculum/learn-expert-escalating-an-issue).

To confirm that #1 is the issue, refer to the instructions in the [Reference Guide](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md) for this particular problem in the Troubleshooting Scenarios section. 

## I'm getting an error about permissions when I'm trying to push my code

Student is out of welcome track and they get an error about permissions when they try to push their code.

You check their SSH with github by asking them to type `ssh -T git@github.com` into their terminal. If they get back something that starts with `Hi learn-ide-user!...` then their SSH with github is not properly set-up.

This can be fixed by [provisioning](https://github.com/learn-co-curriculum/learn-expert-learn-ide-workflow) their account.

## My authentication light did not turn on

*Make sure the student is using Google Chrome.* Lights have been known *not* to trigger if the student is using another browser.

If the authentication light in the welcome track did not turn on, but everything seems like it's in working order (student can get through the edit-me lab in the welcome track), then we may just need to re-trigger the the auth event. 

To do this, have the student [logout of the Learn IDE](#ide-logout) and log back in. This should re-trigger the auth event and turn on the light.

If this does not do the trick, then this issue will need to be [escalated](https://github.com/learn-co-curriculum/learn-expert-escalating-an-issue) as it prevents the student from moving out of the welcome track.

## I cloned a lab but can't see it in the file tree.

Confirm that nothing is syncing by having the user:

1) `cd ~/code`
2) `touch testfile.txt`

If `testfile.txt` shows up in their local file tree, try having the user delete the lab that isn't showing up and re-cloning, or else following the instructions described above for syncing a directory to a new computer. If `testfile.txt` does not show up in their local file tree:

1) Have the user quit and restart the Learn IDE
2) `cd ~/code`
3) `touch testfile2.txt`

If `testfile2.txt` shows up in their local file tree now, have them resync the missing lab. If `testfile2.txt` still doesn't show up, please ping #escalation.

### My lab doesn't clone properly/files do not show up in the file tree

The following steps are sort of troubleshooting 101 for lab issues in the IDE. The most common use case is when the lab has been cloned to the IDE yet the files don't show up in the file-tree/sidebar (although the folder itself may appear or even some of the files).

 - Right-click the problem lab in the tree-view, and select "Resync with Learn IDE Server"
 - If that doesn't do it, or the local folder simply disappears, run Packages > Learn.co > Reconnect (or better yet, manually quit the IDE and re-open) and then attempt to resync again (if the local folder disappeared, you will have to recreate an empty folder locally by the same name, and then you can trigger the resync).

The resync button doesn't destroy anything remotely, so if students are worried that they've lost work, you can assure them it was maintained remotely.

## When I click on the Learn Open button, it opens Atom, but not the IDE

This is a known issue. Close atom. Then open the IDE directly. Then while it is open, click on the learn open button and it should open in the IDE instead of raw atom.

If this is a Windows user that _just_ downloaded or updated the IDE, then take a look at [this](#the-ide-opens-with-no-learnco-package-or-any-command-line).

### The "learn open" button on learn.co isn't working

There are a couple of possibilities as to what is going on here:

1) This is an old user returning to the site and the missed the switch over to the IDE. 

2) This user had previously selected _not_ to open the Learn IDE when clicking the button and the setting is saved.

We can quickly find out what bucket the user is in by asking them if they've recently downloaded the Learn IDE. If they have already downloaded it, it's probably the second issue. If they are not sure or if they confuse the old Mac OS X setup app with the IDE, it's probably a re-activated old user. 

### The 'learn open' command in the IDE is opening the wrong lab

If that is the case, go to learn.co, click on the Octocat icon to open the repository for the lab. Cut and paste the repo name (e.g. for the [gets CLI input lab on fullstack](https://learn.co/tracks/full-stack-web-development/intro-to-ruby-development/command-line-applications/gets-cli-input), click on the Octocat just to the right of the open button to see [the repo](https://github.com/learn-co-students/ruby-gets-input-v-000) and then the command you'd run would be `learn open ruby-gets-input-v-000`. That should open the proper lab and when you run the tests or submit your changes that should update your "current lab" setting in Learn.

## The IDE install isn't triggering lights in the browser

When students install the IDE they go through a process in the browser where the download and authenticate. The lights for this may not be triggering if they do not use Google Chrome.

If this is a Windows user that _just_ downloaded or updated the IDE, then take a look at [this](#the-ide-opens-with-no-learnco-package-or-any-command-line).

## The IDE does not show tree view and `atom <file-name>` opens blank files

When a student is not able to see their tree view in the IDE have them click `View -> Toggle Tree View`.

If they are having issues where they can not see Tree View and open files from the IDE terminal. We have seen success in just removing the local copy of the Learn IDE application, and installing a new version of the application from [learn.co/ide](https://learn.co/ide)

## Other issues

There are a lot of other issues that we haven't included here. Before you esacalate an issue, check out the [Reference Guide](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md#workflow) to see if it's been covered already. If there's an issue that you've been encountering a lot, feel free to make a PR about the issue and what you've found to be a good resolution 

<p class='util--hide'>View <a href='https://learn.co/lessons/learn-expert-ide-troubleshooting'>Learn Expert IDE Troubleshooting</a> on Learn.co and start learning to code for free.</p>
