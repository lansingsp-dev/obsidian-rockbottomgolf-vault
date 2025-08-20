- Link to class - https://learning.swiftotter.com/courses/enrolled/2120532
- Live Store URL - https://lansing.mybigcommerce.com
- Local Store URL - http://localhost:3000
- Browsersync - http://localhost:3002
- Home dashboard - https://store-db5mj43ryi.mybigcommerce.com/manage/dashboard
- See login information in 1Password under BigCommerce Trial
- Stencil CLI Token for Rock Bottom Golf - `g1375eplce9lan2lrhu2e6kwbt1hccd`
- Stencil init 
  ```shell
  stencil init --url `https://lansing.mybigcommerce.com `--token `g1375eplce9lan2lrhu2e6kwbt1hccd`
```
- Stencil CLI - Stencil Command Line Interface.
- Stencil CLI installation - https://developer.bigcommerce.com/docs/storefront/stencil/cli/install
- I installed the Stencil CLI supported version of Node.js
  ```shell
  nvm install 20.18.1
```
- Each time you start a new terminal session and intend to use the Stencil CLI, you must use the `nvm use` command to switch to the appropriate Node.js version.
  ```shell
  nvm use 20.18.1
```
- NPM - Node Package Manager. This is the default package manager for Node.js
- ~~I followed the suggestion from the class and used `lts` which is the latest **long-term support**~~
  ```shell
  nvm install --lts
  nvm use --lts
```
- List all versions of Node.js
  ```shell
  nvm list
```
- See current version of Node.js
  ```shell
  nvm current
```
- Make sure to run stencil from the following directory - `~/dev/projects/bigcommerce-theme-frontend-foundations`
- Make sure to run `nvm use --lts` anytime you open a new terminal window to start the Stencil Server
- Setup terminal to use proper version os Node.js and Install NPM dependencies.
	- If you're new to Node.js/npm, note that this command will install the package dependencies specified in `package.json`, which are not part of your project code but nevertheless required in order for the application to function.
	  ```shell
	  nvm use v20.18.1
	  npm install
```
- To start server
	- 
	  ```shell
	  stencil start
```
- To stop server - `Ctrl+C`
- From here on out, you shouldn't need to repeat the steps for installing the Stencil CLI (unless you start using a different Node.js version) or for initializing the theme (unless bootstrapping a fresh clone/copy). Whenever you begin a new terminal session for local development, just navigate to your theme root directory, switch to the right version of Node.js, and start the server.
- Tunnel. You can start stencil with a tunnel option which allows you to access the server from another machine
  ```shell
  stencil start --tunnel
  
  [Browsersync] Access URLs:
 -------------------------------------------------
       Local: http://localhost:3000
    External: http://192.168.1.104:3000
      Tunnel: https://chubby-mangos-rescue.loca.lt
 -------------------------------------------------
          UI: http://localhost:3002
 UI External: http://localhost:3002
 -------------------------------------------------

```
- To get your tunnel password, you can either:  If running the localtunnel client on a local computer, visit this link in a web browser **on that PC** or any other PC on the same network:`https://loca.lt/mytunnelpassword`
- This will be the password: `38.21.169.224`. Send the temporary Tunnel URL and this password to another user so they can access. This worked fine when  tested get the password on my work MacBook and sent to my personal MacBook and was able to access the site no problem with real store data.