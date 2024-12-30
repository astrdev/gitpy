# Contributing Guide

> *Contributing to the GitPy project is fairly easy. This document shows you how to get started.*

## Prerequisites

First of all, thank you for taking your time to contribute to this project :heart:

But before you start, verify that you meet the following prerequisites:

- You have a code editor, a GitHub account, and experience using command-line programs, including `git` commands and command line options (CLI). You should also be familiar with the [GitFlow workflow][gitflow_url] and Linux environment

- You must read, agree and follow the [Code of Conduct](CODE_OF_CONDUCT.md) AND the [Developer Certificate of Origin (DCO)][DCO_url] in order to contribute to GitPy

- There are a few guidelines that you must follow in order to ease the process of getting your contribution accepted. See [DEVELOPING.md](DEVELOPING.md) for more information

- [OpenPGP][gpg_url] keys is used to sign the Git commits. If you don't know how to sign your commits, please read the [GPG Signing][gpg_signing_url] page

## Getting stared

1. Open a new [**Contributing request issue template**][gitpy_contributing_request_issue_template] and fill it with the necessary information. Now you have to wait until the maintainer review your request and approve your proposed changes

2. If your request is approved, you can fork the project by going on the [GitPy fork][fork_repo_url] page, and <ins>**untick**</ins> the *Copy the master branch only* option then click on the *Create fork* green button

3. In your forked repo., create a new branch based on <ins>**`develop`**</ins>

> [!IMPORTANT]  
> For the branch name, see the [Branch Naming](CODING_GUIDELINES.md#branch-naming) section for more information.

4. After making the first changes, already open a Pull Request from your branch in the forked repo. TO the <ins>**`develop`**</ins> branch on the <ins>**main**</ins> repo. So we know that you're working on it and others people, and us, can help you if needed

	- In your PR, make sure to link the issue you created before in it's description for a better traceability

> [!IMPORTANT]  
> Don't forget, in every commit you will make, to add the Signed-off-by footer trailer by appending the `-s` or `--signoff` option on the `git commit` command or manually add the footer on the commit message like this:
> ```
> foo: baar
>
> description
>
> Signed-off-by: username <email> (keep the `<` and `>`)
> ```

5. After you finished your changes and <ins>**all test was made and all was successful**</ins>, you can ping the maintainer (see the [GitPy Development Team file](DEV-TEAM.md), for the moment, **astrdev** is the only maintainer) on the PR and wait for the review. Don't spam him please, he will review your PR and give you a feedback as soon as possible

6. When your PR is approved, it will be merged into the `develop` branch (on the main repo.) and will be available in the next release

[DCO_url]: https://developercertificate.org/
[gitpy_contributing_request_issue_template]: https://github.com/astrdev/gitpy/issues/new?assignees=astrdev&labels=contributing%2Frequest&projects=astrdev%2Fgitpy&template=3-contributing_request.yml&title=%5BCONTRIBUTING+REQUEST%5D%3A+
[fork_repo_url]: https://github.com/astrdev/gitpy/fork
[gitflow_url]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[gpg_signing_url]: https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification
[gpg_url]: https://gnupg.org/
