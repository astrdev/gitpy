<a name="readme-top"></a>

# GitPy Codebase Structure

> *This is the guide for the GitPy codebase structure. It is important to follow these guidelines in order to have a clean and maintainable codebase.*

<details>
	<summary>Table of Contents</summary>
	<ol>
		<li><a href="#arborescence">Arborescence</a></li>
		<li><a href="#naming-conventions">Naming Conventions</a></li>
			<ul>
				<li><a href="#branch-naming">Branch Naming</a></li>
				<li><a href="#commit-message-formatting">Commit Message Formatting</a></li>
					<ul>
						<li><a href="#commit-types">Commit Types</a></li>
					</ul>
				<li><a href="#version-numbering">Version numbering</a></li>
			</ul>
		<li><a href="#coding-guidelines">Coding Guidelines</a></li>
			<ul>
				<li><a href="#source-files">Source Files</a></li>
				<li><a href="#source-style">Source style</a></li>
			</ul>
	</ol>
</details>

<a name="acronym"></a>

> [!NOTE]  
> SPM = System Packet Manager

## Arborescence

There are several directories in the GitPy project. Here is a brief description of each of them:

| Directory | Description |
| --------: | :---------- |
| [src/](src/) | Root of GitPy |
| [src/commands/](src/commands/) | Files containing operations of CLI's commands of GiPy |
| [src/configs/](src/configs/) | GitPy's config files. The languages used for the these are Python3 and/or Yaml |
| [src/core/](src/core/) | Main core of GitPy. Like the CLI arguments and CLI arg. parsing files |
| [src/databases/](src/databases/) | DB like files. Like the GitPy's versions list in a Yaml file |
| [src/manuals/](src/manuals/) | Unix manpage of GitPy (page that you can have by running `man gitpy`) |
| [src/tools/](src/tools/) | Third party utilities to improve GitPy. If you have a new feature that require a specific third party package/tool version, you can add it here |
| [src/utils/](src/utils/) | Main utilities/snippets of GitPy (home made, not third party) |

> [!NOTE]  
> If your changes require a new directory, you have to inform us in the Contributing request issue you opened and we will tell you if it's okay or not

<p align="right">(<a href="#readme-top">back to top</a>)</p>

----

## Naming Conventions

### Branch Naming

Some branch naming are inspired from the [GitFlow workflow][gitflow_url] branch naming rules with others custom ones. Here is the full branch naming convention used:

| Branch name | Description |
| ----------: | :---------- |
| `master` | The main branch. It's the branch that's MUST BE ALWAY STABLE. This branch should also always contain the latest stable release of the project |
| `develop` | WIP for future releases |
| `feature/<scope>` | Feature in progress and will be merged into the `develop` branch |
| `fix/<scope>` | Fixing a small bug that are not critical and will be merged into the `develop` branch |
| `hotfix/<scope>` | Fixing critical issues in production code and will be merged into the `master` and `develop` branches |
| `release/<version>` | Preparing a new production/stable release and will be merged into the `master` and `develop` branches . Only for stable. -dev, -beta, and -rc versions are tagged  in `develop` branch |
| `docs/<scope>` | Documentation changes and will be merged into the `develop` branch |
| `perf/<scope>` | Performance improvements and will be merged into the `develop` branch |
| `refactor/<scope>` | For cleaning the code and will be merged into the `develop` branch |
| `ci/<scope>` | CI/CD configuration files changes and will be merged into the `develop` branch |

> [!NOTE]  
> If you want to use a different prefix, you just have to tell us in the issue you opened and we will tell you if it's okay or not.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Commit Message Formatting

Each commit message consists of a header, a body and a footer.  The header has a special
format that includes a type, a scope and a description.

> This principe came from the [Conventional Commits][conventional_commits_url] convention.

Here is the commit message convention format:

```
<type>[(optional scope)]: <description>
<BLANK LINE>
[optional body]
<BLANK LINE>
[optional footer(s)]
```

- The optional scope is a phrase describing a section of the codebase enclosed in parenthesis, e.g., "docs(CONTRIBUTING)"

- The description is a short summary of the code changes, e.g., "docs(CONTRIBUTING): Add commit message format section"

- The optional body is a longer description of the code changes. It can be several sentences long

- The optional footer is a place to add some [git footer trailers][git_trailer_doc]

	Here are some examples of trailers that can be used:

	| Trailer | Description |
	| ------: | :---------- |
	| `BREAKING-CHANGE` | Describes a change that breaks backward compatibility or introduces incompatibilities |
	| `Signed-off-by` | Certifies the commit under the [Developer Certificate of Origin (DCO)][DCO_url] |
	| `Co-authored-by` | Credits additional contributors for the commit |
	| `Reviewed-by` | Indicates that the commit has been reviewed and approved |
	| `Acked-by` | Acknowledges the commit without a detailed review |
	| `Tested-by` | Confirms that the commit has been tested and works as expected |
	| `Reported-by` | Attributes the report of a bug or issue to someone |
	| `Closes` | References an issue or ticket that will be closed by this commit |
	| `Fixes` | Specifies a bug or issue resolved by the commit |
	| `Depends-on` | Indicates that the commit relies on another change |
	| `Cherry-picked-from` | Notes that the commit was cherry-picked from another branch |
	| `Reverts` | States that the commit reverts a previous change |
	| `Issue` | Links to a related issue or task without closing it |
	| `Related-to` | Points to a loosely connected issue or ticket |
	| `Change-type` | Describes the type of change (eg, patch, feature, etc) |
	| `Impact` | Specifies the impact or priority of the commit |

<p  align="right">(<a href="#readme-top">back to top</a>)</p>

#### Commit Types

The type must be one of the following:

| Type | Description |
| ---: | :---------- |
| `feat` | A new feature |
| `fix` | A bug Fix |
| `chore` | Used for changes that don't affect the codebase or the user-facing part of the application |
| `docs` | Documentation only changes |
| `refactor` | A code change that neither fixes a bug nor adds a feature. It's used to clean up the code and make it more readable or easier to maintain |
| `perf` | A code change that improves performance |
| `ci` | Changes to our CI configuration files and scripts |
| `revert` | Reverts a previous commit |
| `nic` | For "Not In Changelog", used when the commit doesn't have to be in the changelog (because it generated based on the commit type of `git log`). Can be used when, for example, you already push something and you see after that you forgot to remove some bad typo |

> [!NOTE]
> And also here, if you want to use a different type, you just have to tell us in the issue you opened and we will tell you if it's okay or not.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Version numbering

GitPy use a tree part versioning system separated by dots to represent the major, minor, and patch version numbers. Major version number indicates a significant change or backward-incompatible. Minor version number indicates new features and others small changes that are backward-compatible with previous release. Patch version numbers indicate bug fixes to the previous feature or patch version.

> This principe came from the [Semantic Versioning][semantic_versioning_url] convention.

Production releases use the plain version numbers:

```
MAJOR.MINOR.PATCH
0.1.0
...
...
1.0.0
...
1.1.0
1.4.0
2.0.1
2.3.0
...
```

The initial production release in a MAJOR.MINOR series (MAJOR.MINOR.0) is known as a feature release, which is the only type of release that can introduce new features. Any following production releases within the same MAJOR.MINOR series are restricted to containing only bug fixes.

Development releases are labeled by appending `-dev` to the entire version numbers, followed by the dev. release number:

```
1.0.0-dev1
1.0.2-dev1
1.2.0-dev1
1.2.0-dev2
...
```

Beta-test releases are labeled by appending `-beta` to the entire version numbers, followed by the beta release number:

```
1.0.0-beta1
1.0.2-beta1
1.2.0-beta1
1.2.0-beta2
...
```

Release candidate releases are labeled by appending `-rc` to the entire version numbers, followed by the release candidate number:

```
1.0.0-rc1
1.0.2-rc1
1.2.0-rc1
1.2.0-rc2
...
```

> [!NOTE]  
> A production/stable release will not always have a dev or beta release before itself. It can be directly a RC or a production/stable release.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

----

## Coding Guidelines

### Source Files

The source files name should consist of lowercase ASCII letters, numbers, dash ('-'), underscore ('_') and dot ('.'). to be sure that the files are compatible with different filesystems.

The top of each source file should contain a header with the following information:

1. The Python3 env shebang line.
2. The encoding line.
3. Information about the file
	- Name
	- Created datetime
	- Updated datetime
	- A description
	- Copyright notice
	- License notice

Like this:

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

# Filename: <name>
# Created: YYYY-MM-DDThh:mm:ssZZZZ
# Updated: YYYY-MM-DDThh:mm:ssZZZZ
#
# Description: <description>
#
# Copyright (C) 2024 by astrdev and Contributors. See the file ´CREDITS´ for more information.
#
# Licensed under GNU GPL-3.0 only. See the file ´LICENSE´ for more information.
```

> [!NOTE]  
> The `Created` and `Updated` time format is ISO 8601. `ZZZZ` is stand for the `+/-HH:MM` timezone offset. For example `2024-12-30T05:23:12+0100`.

The file indentation MUST be a tab indentation in size 4. NO spaces for indentation!. It's very important.
For the line length, the formatter will set it to `128` (will be detailed right after).

Source files are formatted via the *[Black (with tabs)][black_w_tabs_url]* and the *[Isort][isort_url]* Python3 formatter together. These two tools are very useful to keep the code clean and readable. If you use *[VScode][vscode_url]* or *[VScode Insider][vscode-insider_url]*, as the *[Black (with tabs)][black_w_tabs_url]* doesn't have it extension, you can install the *[Run on Save][run_on_save_url]* extension with the following commands:

1. First you need to install *[Black (with tabs)][black_w_tabs_url]* and *[Isort][isort_url]* on you machine. To do that, you can use *[pipx][pipx_url]* (or see if your SPM<a href="#acronym">*</a> can install these two tools):

	```shell
	pipx install isort black-with-tabs
	```

2. If you don't have *[pipx][pipx_url]*, then run the following command:

	- If you are on a Debian based distro:

		```shell
		sudo apt update && sudo apt install pipx
		```

	- If you are on a Arch based distro:

		```shell
		sudo pacman -Sy python-pipx
		```

3. Next, open your VScode IDE (Stable or Insider) and open the Quick Open dialog with <kbd>CTRL</kbd> + <kbd>p</kbd> and paste the following command to install the *[Isort][isort_url]* extension:

	```
	ext install ms-python.isort
	```

4. Now create a folder called **.vscode** in the project folder, after create a file called **settings.json** in it, open it an paste the following:

	```jsonc
	{
		"[python]": {
			"editor.codeActionsOnSave": {
				"source.organizeImports": "always"
			},
			"editor.formatOnSave": true
		},
		"editor.detectIndentation": false,
		"editor.indentSize": "tabSize",
		"editor.insertSpaces": false,
		"editor.tabSize": 4,
		"isort.args": [
			"--profile",
			"black"
		]
	}
	```

	This config set to only use tab indent with a size of 4 and format Python file with *[Isort][isort_url]* on save.

5. Finally open the Command Palette with <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>p</kbd>, enter **Preferences: Open User Settings (JSON)**, and in the opened file, add the following to the current config:

	```jsonc
	"emeraldwalk.runonsave": {
		"autoClearConsole": false,
		"commands": [
			{
				"cmd": "black -v --line-length 128 \"${file}\"",
				"match": "\\.py"
			}
		]
	},
	"autoDocstring.docstringFormat": "google",
	"autoDocstring.includeExtendedSummary": true,
	"autoDocstring.includeName": false
	```

	And this config will run the black formatter we installed before on every `.py` file.  

> [!NOTE]  
> These settings cannot be applied in the Workspace settings.json file. For the moment, it can only be set in the User's settings.json file.

And now every time you save a python file (.py) in this project, the formatters will automatically format the code for you.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[DCO_url]: https://developercertificate.org/
[black_w_tabs_url]: https://pypi.org/project/black-with-tabs/
[run_on_save_url]: https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave
[conventional_commits_url]: https://www.conventionalcommits.org/en/v1.0.0/
[gitflow_url]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[isort_url]: https://pypi.org/project/isort/
[semantic_versioning_url]: https://semver.org/
[vscode_url]: https://code.visualstudio.com/
[vscode-insider_url]: https://code.visualstudio.com/insiders/
[pipx_url]: https://pypa.github.io/pipx/
