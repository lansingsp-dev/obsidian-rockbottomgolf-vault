- Files like report.html and theme-bundle.* should not be committed. They are **generated artifacts** from running stencil build or stencil start — so they **change frequently**, even if you didn’t directly modify them.
- Add them to .gitignore

# Ignore Stencil-generated build artifacts (but not your authored files)

- .gitignore Entries
```
# Ignore all Stencil-generated theme bundle JS files
/assets/dist/theme-bundle*

# Ignore Webpack chunks
/assets/dist/*.chunk.*.js
/assets/dist/*.chunk.*.js.LICENSE.txt

# Ignore build report
/assets/dist/report.html

```


Remove them from Git without deleting them locally:
```bash
git rm --cached assets/dist/theme-bundle*
git rm --cached assets/dist/*.chunk.*.js
git rm --cached assets/dist/*.chunk.*.js.LICENSE.txt
git rm --cached assets/dist/report.html
```

> The --cached flag tells Git: “stop tracking this file, but don’t delete it from my working directory.”

Commit the removal:
```bash
git commit -m "Remove generated build files from version control"
```