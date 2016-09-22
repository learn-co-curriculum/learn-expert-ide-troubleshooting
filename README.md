# Troubleshooting IDE and other Technical Issues

As we're building the Learn IDE and improving on it as we go, we run into all sorts of issues with it. We've done a great job on cataloging issues and fixes (we hope you can help us with this as well!).

## Filing Issues

![filing issues](http://i.giphy.com/cJJpP0kjFRTYk.gif)

As a Learn Expert, you hear about a lot of the issues that students run into with the Learn IDE. The development team won't know about these issues though if we don't tell them! Please make sure to use the Report a Bug button when you see an issue with the Learn IDE so we can pass this info on to them.

## Common Issues

There are some common issues we see with the Learn IDE. Here they are in a broad sense, but check out the [support doc](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md) for full bug and solution:

### User sees something different in the Learn IDE terminal than in the file tree

This is usually a syncing issues. The lab probably cloned down properly to the Learn server, but didn't make it all the way to the students local machine. We also sometimes see the student making changes to the lab locally, but the changes are not showing up on the server. Two common solutions here are right clicking on the files and selecting 'Re-sync' or just using `rm -rf` on that lab and having the student re-clone.

### User is seeing 'No passwd' in the Learn IDE terminal or cannot push code

This is an issue setting up their Learn IDE account on the server. We have a really cool tool called [Provisioning](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md#provision-an-account) that lets us non-destructively set up a users account. There's two options when provisioning, one for students that should not yet be connected with github, and one for students whose accounts did not get properly setup with github.

Please refer to [this document in the Reference Guide](https://github.com/flatiron-labs/learn-support/blob/master/learn-ide.md) as you run into these issues and if you solve anything that isn't documented, please put in a pull request to the repo to add it!
