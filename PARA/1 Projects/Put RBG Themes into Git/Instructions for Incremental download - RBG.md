
### **Step 1: Create the Working Folders**

```bash
mkdir ~/bigcommerce-theme-history
cd ~/bigcommerce-theme-history

mkdir versions          # Extracted theme folders
mkdir ~/dev/projects/rbg-bigcommerce-theme              # The Git repo you'll build
```


### **Step 2: Create a New Git Repository**
```bash
cd ~/dev/projects/rbg-bigcommerce-theme
git init
```

- Create `.gitignore` file
	- [[gitignore instructions]]
### **Step 3: Copy First Version and Commit**
```bash
cd ~/dev/projects/rbg-bigcommerce-theme
cp -r ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_04-23-25_pb-discount-pricing-1/* .
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
git commit -m "Initial commit: RBG_ZE_04-23-25_pb-discount-pricing-1"
```

### **Step 5: Copy next version over the repository
```bash
cd ~/dev/projects/rbg-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git" ~/dev/bigcommerce-RBG-theme-history/versions/RBG_DF_04-25-25_launch-pagination-update-1/* .

# Open WebStorm to make sure the changed list of files are just legitimate source file that we want Git to track.

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DF_04-25-25_launch-pagination-update-1"

```

----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-02-25_html-tag-updates-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-02-25_html-tag-updates-1"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-02-25_ball-personalization-bp-old-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-02-25_ball-personalization-bp-old-1"
```

---------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-02-25_ball-personalization-bp-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-02-25_ball-personalization-bp-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_DM_05-08-25_heroNoFollow-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DM_05-08-25_heroNoFollow-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-16-25_more_brand_carousels-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-16-25_more_brand_carousels-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-22-25_category-cta-slider-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-22-25_category-cta-slider-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_05-23-25_category-cta-slider-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_05-23-25_category-cta-slider-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-02-25_category-cta-slider-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-02-25_category-cta-slider-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-03-25_category-cta-slider-old-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-03-25_category-cta-slider-old-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-03-25_category-cta-slider-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-03-25_category-cta-slider-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_DM_06-09-25_brand+breadcrumbs-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DM_06-09-25_brand+breadcrumbs-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-16-25_menu-updates-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-16-25_menu-updates-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-18-25_menu-updates-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-18-25_menu-updates-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-19-25_temp-template-removal-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-19-25_temp-template-removal-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_06-25-25_pulse-thumbnail-testing-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_06-25-25_pulse-thumbnail-testing-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_DF_06-25-25_pulse-thumbnail-and-button-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DF_06-25-25_pulse-thumbnail-and-button-1"
```

-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_ZE_07-01-25_add-client-css-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_ZE_07-01-25_add-client-css-1"
```


-----------
```bash
# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_DF_07-14-25_accessibility-audit-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_DF_07-14-25_accessibility-audit-1"
```

-----------
```bash
cd ~/dev/projects/rbg-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_CL_07-23-25_Osano-Launch-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_CL_07-23-25_Osano-Launch-1"
```

--------

```bash
cd ~/dev/projects/rbg-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_CL_07-23-25_Osano-Launch-SPL-Changes-1/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_CL_07-23-25_Osano-Launch-SPL-Changes-1"
```

```bash
cd ~/dev/projects/rbg-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_CL_07-23-25_Osano-Launch-1-2/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_CL_07-23-25_Osano-Launch-1-2. A lot of updates to DynamicYield and Osano"
```

```bash
cd ~/dev/projects/rbg-bigcommerce-theme

# Copy next version over the repository
rsync -av --delete --exclude=".git"  ~/dev/bigcommerce-RBG-theme-history/versions/RBG_CL_07-23-25_Osano-Launch-1-3/* .

# Stage everything, including deletions. Adds new, modified, and deleted files
git add --all

# Commit
git commit -m "Update to theme version RBG_CL_07-23-25_Osano-Launch-1-2. A lot of updates to DynamicYield and Osano"
```