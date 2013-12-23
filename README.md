![Imhotep](https://f.cloud.github.com/assets/37303/1799404/d09d070a-6b99-11e3-9b31-f7eb9c5a2245.png)
# Imhotep, the peaceful builder.

## What is it?
Imhotep is a tool which will comment on commits coming into your
repository and check for syntactic errors and general lint
warnings. 

## Installation

Currently, installation is done from source through Python packaging
system. We first need to download it from GitHub. We then setup a
virtualenv which will keep our python packages separate from other
things on your system, lest we have version conflicts. Finally, we
install the required packages.

```
git clone git://github.com/justinabrahms/imhotep.git
virtualenv env
. env/bin/activate
pip install -r requirements.txt
```

## Usage

To use imhotep, we must tell it which repository to look at, who to
authenticate as and what to comment on. Imhotep is able to comment in
two ways: either on a single commit or on a pull request.


### Commenting on a pull request
```
python imhotep.py \
       --repo_name="justinabrahms/imhotep" \
       --github-username="imhotepbot" \
       --github-password="a_sha_generated_by_github" \
       --pr-number=1
```

### Commenting on a single commit
```
python imhotep.py \
       --repo_name="justinabrahms/imhotep" \
       --github-username="imhotepbot" \
       --github-password="a_sha_generated_by_github" \
       --commit="a123445714cfa89d1e843d9950ea8f249cd6e4df"
```

### Full Usage Info
```
usage: imhotep.py [-h] --repo_name REPO_NAME [--commit COMMIT]
                  [--origin-commit ORIGIN_COMMIT]
                  [--filenames FILENAMES [FILENAMES ...]] [--debug]
                  --github-username GITHUB_USERNAME --github-password
                  GITHUB_PASSWORD [--no-post] [--authenticated]
                  [--pr-number PR_NUMBER]

Posts static analysis results to github.

optional arguments:
  -h, --help            show this help message and exit
  --repo_name REPO_NAME
                        Github repository name in owner/repo format
  --commit COMMIT       The sha of the commit to run static analysis on.
  --origin-commit ORIGIN_COMMIT
                        Commit to use as the comparison point.
  --filenames FILENAMES [FILENAMES ...]
                        filenames you want static analysis to be limited to.
  --debug               Will dump debugging output and won't clean up after
                        itself.
  --github-username GITHUB_USERNAME
                        Github user to post comments as.
  --github-password GITHUB_PASSWORD
                        Github password for the above user.
  --no-post             [DEBUG] will print out comments rather than posting to
                        github.
  --authenticated       Indicates the repository requires authentication
  --pr-number PR_NUMBER
                        Number of the pull request to comment on
```

## Linter Support

There is currently support for 2 linters: PyLint and JSHint. If it
finds violations, it will post those violations to GitHub. New linting
tools are encouraged!

## What's with the name?

Imhotep, the first Egyptian architect, is known as "the one who comes
in peace". In keeping with that name, the goal of this tool is to keep
code reviews peaceful and productive by having robots point out the
nitpicky details, leaving people to critique bigger picture things,
not spacing and misspelling issues.
