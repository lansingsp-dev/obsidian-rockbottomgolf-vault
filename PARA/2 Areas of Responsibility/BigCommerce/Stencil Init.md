- Rock Bottom Golf
	- 
	  ```shell
	  cd ~/dev/projects/rbg-bigcommerce-theme
	  nvm use v20.18.1
	  npm install
```
	- Command to initialize locally running stencil:
		- stencil init  (See BigCommerceAPI Credentials in 1Password for OAuth Access Token)
		  ```shell
		  stencil init --url `https://www.rockbottomgolf.com` --token `xxx`
```
	- When asked - `What is your favourite Package Manager?` select `npm`
	- When starting stencil with `stencil start` use the channel - `https://www.rockbottomgolf.com`
- Rock Bottom Golf Demo
	- 
	  ```shell
	  cd ~/dev/projects/rbg-demo-bigcommerce-theme
	  nvm use v20.18.1
	  npm install
```
	- stencil init (See BigCommerceAPI Credentials in 1Password for OAuth Access Token)
	  ```shell
	  stencil init --url `https://rockbottomgolf2.com` --token `xxx`
```
	- When asked - `What is your favourite Package Manager?` select `npm`
	- When starting stencil with `stencil start` use the channel - `https://rockbottomgolf2.com`

Golf Bags Demo

```shell
cd ~/dev/projects/golf-bags-demo-theme
nvm use v20.18.1
stencil init --url https://golf-bags.mybigcommerce.com --token 29wjswxt0gfqbrw1amy3waryxy2a9v9 --port 3000
```