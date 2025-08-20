
### **Step 1: Create the Working Folders**

```bash
mkdir ~/bigcommerce-Golf-Bags-theme-history
cd ~/bigcommerce-Golf-Bags-theme-history

mkdir versions          # Extracted theme folders
mkdir ~/dev/projects/golf-bags-bigcommerce-theme              # The Git repo you'll build
```


### **Step 2: Create a New Git Repository**
```bash
cd ~/dev/projects/golf-bags-bigcommerce-theme
git init
```

- Create `.gitignore` file
	- [[gitignore instructions]]

### **Step 3: Copy First Version and Commit**
```bash
cd ~/dev/projects/golf-bags-bigcommerce-theme
cp -r ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DF_2025-03-31_Header-Navigation-Fix-6/* .
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
git commit -m "Initial commit: GolfBags_DF_2025-03-31_Header-Navigation-Fix-6"
```

- Open new project in WebStorm to make sure opens ok
- Close WebStorm

### **Step 5: Copy next version over the repository
```bash
cd ~/dev/projects/golf-bags-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git" ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_04-01-25_couponText-pdpFields-6/* .

# Open WebStorm to make sure the changed list of files are just legitimate source file that we want Git to track.

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_04-01-25_couponText&pdpFields-6"

```

----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DF_04-07-25_pulseButtonTesting-02-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DF_04-07-25_pulseButtonTesting-02-6"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_04-07-25_Header-Navigation-Fix-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_04-07-25_Header-Navigation-Fix-6"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DF_04-08-25_Pulse-Button-Fixed-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DF_04-08-25_Pulse-Button-Fixed-6"
```


-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_04-09-25_personalizationMessage-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_04-09-25_personalizationMessage-6"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_04-10-25_personalizationMessage-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_04-10-25_personalizationMessage-6"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-04-14_klevu-update-product-review-count-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-04-14_klevu-update-product-review-count-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-04-30_klevu-review-and-tabs-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-04-30_klevu-review-and-tabs-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-05-01_klevu-review-redirect-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-05-01_klevu-review-redirect-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-05-02_klevu-review-redirect-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-05-02_klevu-review-redirect-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-05-02_klevu-review-redirect-v1-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-05-02_klevu-review-redirect-v1-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_06-03-25_multipleUpdates-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_06-03-25_multipleUpdates-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_06-05-25_multipleUpdates-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_06-05-25_multipleUpdates-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DM_06-10-25_multipleUpdates-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DM_06-10-25_multipleUpdates-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_06-26-25_shopper-approved-hotfix-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_06-26-25_shopper-approved-hotfix-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_DF_07-02-25_Pulse-Fix-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_DF_07-02-25_Pulse-Fix-6"
```

-----------

```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_MILL_2025-07-07_site-health-klevu-scripts-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_MILL_2025-07-07_site-health-klevu-scripts-6"
```

-----------


```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-Golf-Bags-theme-history/versions/GolfBags_ZE_07-31-2025_add_shipping_msg-6/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version GolfBags_ZE_07-31-2025_add_shipping_msg-6"
```

-----------
