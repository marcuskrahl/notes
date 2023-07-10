
Ignore commits which are just maintenance like formatting/moving files

```bash
git blame --ignore-rev a34b25c23 index.html
```

Ignored commits can be added to a file to ignore in bulk

```bash
git blame --ignore-revs-file .git-blame-ignore-revs index.html
```

Ignore file can be used by default for all blames (even in editors)

```bash
git config blame.ignoreRevsFile .git-blame-ignore-revs
```


The name `.git-blame-ignore-revs` is a standard name and is automatically picked up by some tools, e.g. github