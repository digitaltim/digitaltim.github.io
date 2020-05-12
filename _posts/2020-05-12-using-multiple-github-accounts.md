---
layout: post
title: "Using Multiple GitHub Accounts"
date: 2020-05-12
---

I have a few different GitHub accounts which clash in my Windows environment typically when I am ready to push to GitHub with `git push`. It's not a huge deal but I don't get prompted for a username/password because there's already one stored on my system associated with another repo. I suppose I could setup things a little differently but I haven't yet felt enough pain to reconsider my overall approach for managing things **most** efficiently. As such I resort to solving the problem via a Google search, which typically leads me to Stack Overflow.

Maybe I should also mention I first start to sense there's a problem when I make my first commit to a repo that's been freshly checked out and see this message:

    Your name and email address were configured automatically based
    on your username and hostname. Please check that they are accurate.
    You can suppress this message by setting them explicitly:

        git config --global user.name "Your Name"
        git config --global user.email you@example.com

    After doing this, you may fix the identity used for this commit with:

        git commit --amend --reset-author

I've done this enough times to realize that I don't want to set the name and email globally in the `~/.gitconfig` file. [^1] Omitting the `--global` option sets the repository's `.git/config` file as the default behavior. Once this is done, along with `git commit --amend --reset-author`, one might think the problem is solved. Yet it's not, because of how Git Bash stores passwords for remote repos. Thus I see the problem to solve now happens on push:

    $ git push
    remote: Permission to digitaltim/digitaltim.github.io.git denied to <other repo username>.
    fatal: unable to access 'https://github.com/digitaltim/digitaltim.github.io.git/':
    The requested URL returned error: 403

The solution for now is to reset the external credential helper  `git config --local credential.helper ""`.[^2] The next attempt to `git push` prompts me for a new username and password. Although I'm tempted to go deeper, I'll have to leave that for anther day...[^3]

[^1]: [git-config](https://git-scm.com/docs/git-config "Get and set repository or global options")
[^2]: [How do I push to GitHub under a different username?](https://stackoverflow.com/questions/13103083/how-do-i-push-to-github-under-a-different-username "git config --local credential.helper "" may do the trick.")
[^3]: [Setting your commit email address](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address "You can set a primary email address on GitHub that's associated with web-based Git operations you perform such as edits and merges.")

