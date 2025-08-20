
### **Step 1: Create the Working Folders**

```bash
mkdir ~/bigcommerce-RBG-demo-theme-history
cd ~/bigcommerce-RBG-demo-theme-history

mkdir versions          # Extracted theme folders
mkdir ~/dev/projects/rbg-demo-bigcommerce-theme              # The Git repo you'll build
```


### **Step 2: Create a New Git Repository**
```bash
cd ~/dev/projects/rbg-demo-bigcommerce-theme
git init
```

- Create `.gitignore` file
	- [[gitignore instructions]]

### **Step 3: Copy First Version and Commit**
```bash
cd ~/dev/projects/rbg-demo-bigcommerce-theme
cp -r ~/dev/bigcommerce-RBG-demo-theme-history/versions/rockBottomGolf_03-01-21_demoBuild-1/* .
```

- Install `node.js` dependencies defined in package.json
  ```shell
nvm use v20.18.1
npm install
```


- Add and commit to Git
```shell
git config --global core.autocrlf input
git add .
git commit -m "Initial commit: rockBottomGolf_03-01-21_demoBuild-1"
```

### **Step 5: Copy next version over the repository
```bash
cd ~/dev/projects/rbg-demo-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git" ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_ZE_03-09-21_dy-and-other-scripts-1/* .

# Open WebStorm to make sure the changed list of files are just legitimate source file that we want Git to track.

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_03-09-21_dy-and-other-scripts-1"

```

----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_ZE_03-11-21_dy-and-other-scripts-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_03-11-21_dy-and-other-scripts-1"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_ZE_06-09-22-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-09-22-1"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_CL_08-02-24_crypto-package-hotfix-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_CL_08-02-24_crypto-package-hotfix-1"
```


-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_DM_04-02-25_pdpInfo-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DM_04-02-25_pdpInfo-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_DM_04-02-25_pdpInfo-1-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DM_04-02-25_pdpInfo-1-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-demo-theme-history/versions/RBG_DF_10-22-24_Pulse-Slideout-Update_2-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DF_10-22-24_Pulse-Slideout-Update_2-1"
```

-----------
