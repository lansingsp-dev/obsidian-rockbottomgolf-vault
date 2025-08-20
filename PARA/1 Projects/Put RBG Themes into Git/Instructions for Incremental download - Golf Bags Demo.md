
### **Step 1: Create the Working Folders**

```bash
mkdir ~/bigcommerce-Golf-Bags-Demo-theme-history
cd ~/bigcommerce-Golf-Bags-Demo-theme-history
mkdir versions          # Extracted theme folders

mkdir ~/dev/projects/golf-bags-demo-bigcommerce-theme              # The Git repo you'll build
```


### **Step 2: Create a New Git Repository**
```bash
cd ~/dev/projects/golf-bags-demo-bigcommerce-theme
git init
```

- Create `.gitignore` file
	- [[gitignore instructions]]

### **Step 3: Copy First Version and Commit**
```bash
cd ~/dev/projects/golf-bags-demo-bigcommerce-theme
cp -r ~/dev/bigcommerce-Golf-Bags-Demo-theme-history/versions/GolfBags_ZE_07-31-2025_add_shipping_msg-6/* .
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
git commit -m "Initial commit: GolfBags_ZE_07-31-2025_add_shipping_msg-6"
```

- Open new project in WebStorm to make sure opens ok
- Close WebStorm

### **Step 5: Copy next version over the repository
```bash
cd ~/dev/projects/golf-bags-demo-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git" ~/dev/bigcommerce-Golf-Bags-Demo-theme-history/versions/GolfBags_DM_04-01-25_couponText-pdpFields-6/* .

# Open WebStorm to make sure the changed list of files are just legitimate source file that we want Git to track.

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_04-01-25_couponText&pdpFields-6"

```
