# gometalinter-pre-commit
Basic git pre-commit hook that runs [`gometalinter`](https://github.com/alecthomas/gometalinter) for all files staged for commit. When the linter raises any issues, the hook requires confirmation before proceeding with the commit.

# Install
Installation is easy. Just save [`pre-commit`](pre-commit) to your repository's hooks directory and make sure it has permissions to execute. The file should typically be at `.git/hooks/pre-commit` (relative to your repository, obviously).

```bash
cd /path/to/your/repo
curl -S https://raw.githubusercontent.com/epels/gometalinter-pre-commit/master/pre-commit > .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

Note: this will overwrite your existing `pre-commit` hook, if you have one.

# Example
```bash
$ git add main.go
$ git commit -m "Some message"
gometalinter raised issues:
main.go:5:6:warning: func someUnusedFunc is unused (U1000) (megacheck)
Would you like to proceed committing? (y/n) n
Aborting commit
```

# Caveats
* If you `git add` a file and modify it afterwards, it will run the linter for the current state.