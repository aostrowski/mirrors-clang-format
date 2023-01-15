clang-format mirror for checking diffs
======================================

Yet another mirror of the `clang-format` package for the pre-commit tool.

As opposed to https://github.com/pre-commit/mirrors-clang-format/ (which we
forked from), this one verifies the diffs instead of whole files. You'd expect
that from clang-format-diff, but the tool that does the work, comes with
clang-format and nicely integrates with git is cleverly named git-clang-format,
so this is what this repo's hook uses and hence this is how it's named.

For more info on pre-commit, see: https://github.com/pre-commit/pre-commit

For more info on clang-format, see: https://github.com/ssciwr/clang-format-wheel

### Using git-clang-format with pre-commit

Add this to your `.pre-commit-config.yaml`:

```yaml
-   repo: https://github.com/aostrowski/pre-commit-mirror-git-clang-format
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: git-clang-format
```

### Implementation details

The tags for each clang-format version are generated automatically using the
[pre-commit-mirror tool](https://github.com/pre-commit/pre-commit-mirror-maker).
You can see the command invocation in
[.github/workflows/main.yml](.github/workflows/main.yml).

As of writing this, the tool didn't yet support adding multiple hooks in one
repo, so if you wish to add another one, either improve the tool or just create
another fork.
