# Using latexdiff for track change

## installing latexdiff with git integration

```bash
sudo apt install latexdiff
sudo apt install asciidoc
git clone https://gitlab.com/git-latexdiff/git-latexdiff.git
cd git-latexdiff
sudo make install
```

## using git latexdiff

one can see the difference between the current status of the repository compared with any previous commit.
this can be done by simply executing

```bash
git latexdiff <commit name>
```

where `<commit name>` can be the commit hash, a position relative to the head (such as `HEAD~2` for the second to last commit) or a tag.
Once executed it will generate on the fly the pdf with all the differences highlighted.

## keeping track of the latest version that has been checked
A simple way to see the difference compared to the latest read version, very useful when there are a lot of small commits, is to use tags to reference which commit is the lastest read.
This commit will be local to the user, so there is not issues with overlaps unless it is pushed to the remote (but there is no reason to do so).

one can create a tag, for example `latest` with the command

`git tag latest`

that will automatically tag the lastest commit as the one of interest.
Once created, one needs to update which is the lastest commit to the current one, and this can be done simply by calling

`git tag -f latest`

Each one of these commands can also take a commit name to indicate a specific commit instead of the latest one.

at this point one can see the difference with the lastest read commit using:

`git latexdiff latest`
