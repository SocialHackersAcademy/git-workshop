# GIT Workshop

## History[<sup>1</sup>](#references)

Git was created by Linus Torvalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development. Since 2005, Junio Hamano has been the core maintainer.

## Naming[<sup>1</sup>](#references)

Torvalds sarcastically quipped about the name git (which means "unpleasant person" in British English slang): "I'm an egotistical bastard, and I name all my projects after myself. First 'Linux', now 'git'."
The man page describes Git as "the stupid content tracker". The read-me file of the source code elaborates further:

"git" can mean anything, depending on your mood.

- Random three-letter combination that is pronounceable, and not actually used by any common UNIX command. The fact that it is a mispronunciation of "get" may or may not be relevant.
- Stupid. Contemptible and despicable. Simple. Take your pick from the dictionary of slang.
- "Global information tracker": you're in a good mood, and it actually works for you. Angels sing, and a light suddenly fills the room.
- "Goddamn idiotic truckload of sh\*t": when it breaks.

## System, global & project configurations[<sup>2,3,4</sup>](#references)

Priority for configuration levels is: local, global, system. This means when looking for a configuration value, Git will start at the local level and bubble up to the system level.

```sh
$ git config [<file-option>]
```

- `--local` : By default, git config will write to a local level if no configuration option is passed. Local level configuration is applied to the context repository git config gets invoked in. Local configuration values are stored in a file that can be found in the repo's .git directory: `.git/config`

- `--global`: Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. `~ /.gitconfig` on Unix systems and `C:\Users\\.gitconfig` on Windows

- `--system`: System-level configuration is applied across an entire machine. This covers all users on an operating system and all repos. The system level configuration file lives in a gitconfig file off the system root path. `$(prefix)/etc/gitconfig` on unix systems. On windows this file can be found at `C:\Documents and Settings\All Users\Application Data\Git\config` on Windows XP, and in `C:\ProgramData\Git\config` on Windows Vista and newer.

### Editing

```sh
# Directly edit a value
$ git config user.email "your_email@example.com" # This will edit the local configuration by default
$ git config --global user.email "your_email@example.com"

# Open the config file and edit it through your console
$ git config --global -e

# Otherwise use an editor, locate and open the respective file
```

## Branching[<sup>5,6</sup>](#references)

There are several branching strategies, but we'll briefly see the basics of Gitflow since it's the most popular.

- `main` (or `master): We consider origin/master to be the main branch where the source code of HEAD always reflects a production-ready state.
- `develop`: We consider origin/develop to be the main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release.
- `feature/<feature-description>` :Feature branches (or sometimes called topic branches) are used to develop new features for the upcoming or a distant future release.

There are also other categories described by [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/) like `release` and `hotfix`

[And also more branching strategies](https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy)

## Commit messages[<sup>7,8</sup>](#references)

Most common rules:

- Separate subject from body with a blank line
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how

Sample:

```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```

Another approach on the commit message is the [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

Sample:

```
feat: Update cities enumeration
```

## Pull requests and reviews[<sup>9,10,11</sup>](#references)

Keep these in mind when doing a pull request:

- Separate your commits by layer or functional steps
- The code at each step (commit) should be functional
- Avoid fix commits
- Have in mind the reviewer
- Focus only on one task (specific feature/bug fix/optimization etc.) on your branch and your pull request
- Review your own code before you officially put it up for review.
- Write a summary for the code you introduce and the problem it handles

Keep these in mind when reviewing code:

- Technical facts and data overrule opinions and personal preferences.
- Code should have good functionality
- Code should have low complexity
- Code should have low volume
- Code should have good naming (variables, methods, classes, files etc.)
- Code should have comments on tricky pieces of code
- The developer isn’t implementing things they might need in the future but don’t know they need now.
- It's OK not to approve and ask for changes

When commenting:

- Never leave comments or suggestions on things your are not familiar with
- Be polite
- Give constructive feedback and guidance
- Provide technical insight (links, explanation etc.) on your suggestions
- Provide code sample suggestions
- Give praise for the good stuff!

## Merging[<sup>12,13,14</sup>](#references)

The type of merging relies heavily on the branching model your team uses. Still [here](https://docs.github.com/en/github/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges) is some explanation on the Github merge options and how they work

## Bonus

- [Rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase#:~:text=What%20is%20git%20rebase?,of%20a%20feature%20branching%20workflow.)
- [Fixups & autosquash](https://fle.github.io/git-tip-keep-your-branch-clean-with-fixup-and-autosquash.html)
- [GIT Hooks](https://www.atlassian.com/git/tutorials/git-hooks)

<hr />

## References

1. https://en.wikipedia.org/wiki/Git
2. https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration
3. https://git-scm.com/docs/git-config
4. https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config
5. https://nvie.com/posts/a-successful-git-branching-model/
6. https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy
7. https://chris.beams.io/posts/git-commit/
8. https://www.conventionalcommits.org/en/v1.0.0/
9. https://google.github.io/eng-practices/review/reviewer/
10. https://hackernoon.com/how-to-give-and-get-better-code-reviews-e011c3cda55e
11. https://stackoverflow.blog/2019/09/30/how-to-make-good-code-reviews-better/
12. https://git-scm.com/docs/git-merge
13. https://docs.github.com/en/github/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges
14. https://www.atlassian.com/git/tutorials/merging-vs-rebasing

