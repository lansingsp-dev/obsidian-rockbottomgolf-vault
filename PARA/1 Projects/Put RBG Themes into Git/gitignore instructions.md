
- Add directories and files.
	- For directories add through WebStorm right click
		- Right Click on node_modules 
			- Right Click > Git Add to .gitignore. First time it will need to create .gitignore. Also add .gitignore to git
	- You mad need to exclude directories from indexing and search

.gitignore
```
# ================================  
# Node.js / NPM Dependencies  
# ================================  
node_modules/  
npm-debug.log*  
yarn-debug.log*  
yarn-error.log*  
package-lock.json  
  
# ================================  
# BigCommerce Stencil Build Artifacts  
# ================================  
parsed/  
assets/dist/  
*.zip  
  
# ================================  
# Stencil CLI Configuration  
# ================================  
config.json  
config.stencil.json  
secrets.stencil.json  
stencil.conf.js  
stencil.conf.cjs  
  
# ================================  
# WebStorm / JetBrains IDEs  
# ================================  
.idea/  
*.iml  
  
# ================================  
# Logs  
# ================================  
*.log
```

- Remove from Git without deleting them locally. Run these from the WebStorm terminal. Only need to do this if they were accidentally added to Git.
	- 
	  ```bash
	git rm -r --cached node_modules
	git rm -r --cached parsed/
	git rm -r --cached .idea
	
	git rm --cached assets/dist/theme-bundle*
	git rm --cached assets/dist/*.chunk.*.js
	git rm --cached assets/dist/*.chunk.*.js.LICENSE.txt
	git rm --cached assets/dist/report.html

    git commit -m "gitignore updates"
```

- `git rm -r --cached` - This command
	- Stop tracking directory/files in git
	- But don't delete the frile from disk
	-  If it’s in .gitignore, it will stay ignored on future changes
- `git commit -m "gitignore updates"` - Can do from WebStorm terminal or the WebStorm commit window.
- 