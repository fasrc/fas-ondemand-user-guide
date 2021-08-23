# Rstudio Server

## Getting started with Rstudio

1. On the menu bar, click `Interactive Apps` and select RStudio app for your class. For example, if your class is Gov 50, select `RStudio Server - Gov50`.<br/>
![Select-rstudio-App screenshot](images/select-rstudio-app.png?raw=true)

2. Click `Launch`.<br/>
![Launch-rstudio-server screenshot](images/launch-rstudio-server.png?raw=true)

3. On the page that follows, click `Connect to Rstudio Server`.<br/>
![Connect-to-rstudio-server screenshot](images/connect-to-rstudio-server.png?raw=true)

4. A new browser tab with Rstudio will open.<br/> 
![Rstudio-interface screenshot](images/rstudio-interface.png?raw=true)

## Working with Rstudio

### How to restart Rstudio

_Before you restart, make sure any programs and data files that you want to preserve have been saved to your home directory._

To restart your Rstudio server completely, follow these steps:

1. Navigate to `My Interactive Sessions` in FAS OnDemand.<br/>
![Navigate-to-interactive-sessions.png screenshot](images/navigate-to-interactive-sessions.png?raw=true)

2. Click `Delete` to remove your Rstudio server.<br/>
![Stop-rstudio-server.png screenshot](images/stop-rstudio-server.png?raw=true)

3. Click `Confirm`.<br/>
![confirm-delete-rstudio-session.png screenshot](images/confirm-delete-rstudio-session.png?raw=true)
<br/>
![after-delete-no-active-rstudio-sessions.png screenshot](images/after-delete-no-active-rstudio-sessions.png?raw=true)

4. Select the Rstudio app and launch a new server.<br/>
![Launch-rstudio-server.png screenshot](images/launch-rstudio-server.png?raw=true)

### How to install R packages

Rstudio server comes preinstalled with most if not all packages required for your class, so if you can't find the package in the list of installed packages, make sure that you are connecting to the correct Rstudio app for your class before proceeding (e.g. `Rstudio Server - Gov50`).

In the event that you need to install additional R packages, you can install from CRAN or github as follows:
- CRAN: `install.packages('packagename')` 
- Github: `remotes::install_github('user/packagename')`

For example, to install the [shiny](https://cran.r-project.org/web/packages/shiny/index.html) package, run `install.packages('shiny')`:

![Install-r-packages.png screenshot](images/install-r-packages.png?raw=true)

The packages will be installed to the `R` folder of your home directory. 

### How to connect Rstudio to github with HTTPS

Follow the steps below to connect Rstudio to github with HTTPS:

1. Open a new browser tab and visit [https://github.com/settings/tokens](https://github.com/settings/tokens). You may be prompted to login to your github account.<br/>

2. Click `Generate new token`.<br/>
![github-personal-acces-tokens.png screenshot](images/github-personal-acces-tokens.png?raw=true)

3. Enter a **Note** (e.g. your course name), select **repo** scope(full control of private repositories), and then click `Generate token`.<br/>
![github-generate-new-token.png screenshot](images/github-generate-new-token.png?raw=true)
<br/>
![github-generate-new-token-submit.png screenshot](images/github-generate-new-token-submit.png?raw=true)

4. Copy this token or _PAT_ to your clipboard (click the clipboard icon).<br/>
![github-personal-access-token-generated.png screenshot](images/github-personal-access-token-generated.png?raw=true)

5. In Rstudio, define an environment variable in `.Renviron` named `GITHUB_PAT` by following these steps:<br/>

    a. Enter the following in your **Console**:<br/>

    ```r
    library(usethis)
    edit_r_environ()
    ```

    b. Add the `GITHUB_PAT` environment variable to `.Renviron`:<br/>

    ```
    GITHUB_PAT=PasteYourTokenHere
    ```

    ![github-add-pat-to-renviron.png screenshot](images/github-add-pat-to-renviron.png?raw=true)

    c. Save `.Renviron` and then close it.<br/>

    ![github-add-pat-to-renviron-save.png screenshot](images/github-add-pat-to-renviron-save.png?raw=true)

6. In Rstudio, set your git credentials. Enter the following in your **Console**, and when prompted, enter your _PAT_ for the password.<br/>
    
    ```
    library(credentials)
    credential_helper_set("store", global = TRUE)
    git_credential_ask('https://github.com')
    ```
    
    _Note_: this will update `.gitconfig` and `.git-credentials` in your home directory.
    
7. Now you should be able to _Create a Project from Version Control_ in RStudio using the HTTPS URL from github as the `Repository URL`.<br/>

### How to connect Rstudio to github with SSH

Follow the steps below to connect Rstudio to github with SSH:

1. Connect to Rstudio and navigate to `Tools > Global Options`.<br/>
![Rstudio-navigate-to-global-options.png screenshot](images/rstudio-navigate-to-global-options.png?raw=true)

2. Select the options for `Git/SVN`.<br/>
![Rstudio-global-options-git.png screenshot](images/rstudio-global-options-git.png?raw=true)

3. Click `View public key`. _Note: this key is automatically created for you when you first login to FAS OnDemand._<br/>
![Rstudio-global-options-git-view-public-key.png screenshot](images/rstudio-global-options-git-view-public-key.png?raw=true)

4. Copy the key to your clipboard. Everything in the box needs to be copied, starting with `ssh-rsa ...`.<br/>
![Rstudio-global-options-git-view-public-key-details.png screenshot](images/rstudio-global-options-git-view-public-key-details.png?raw=true)

5. Open a new browser tab and visit [https://github.com/settings/keys](https://github.com/settings/keys). You may be prompted to login to your github account.<br/>

6. Click `New SSH key`.
    - For `Title`, enter a descriptive name (e.g. `OnDemand GOV50`).
    - For `Key`, paste the public key that you previously copied to your clipboard (see steps 3-4). <br/>
    - Then click `Add SSH key`. <br/>
![Github-add-new-public-key.png screenshot](images/github-add-new-public-key.png?raw=true) <br/>
![Github-view-ssh-keys.png screenshot](images/github-view-ssh-keys.png?raw=true)

7. Now you should be able to _Create a Project from Version Control_ in RStudio using the SSH URL from github as the `Repository URL`.<br/>

    ![github-clone-switch-to-ssh.png screenshot](images/github-clone-switch-to-ssh.png?raw=true)<br/>
    ![github-clone-ssh-url.png screenshot](images/github-clone-ssh-url.png?raw=true)


## Troubleshooting Rstudio

### Rstudio will not start

If Rstudio will not start and you get an error message like this:

![sbatch-error-on-launch.png screenshot](images/sbatch-error-on-launch.png?raw=true)

Wait 2-3 minutes and try to re-launch the application. This may happen the very first time you login to FAS OnDemand and your account hasn't been fully provisioned yet.

If you continue to get this error or otherwise cannot start Rstudio, please contact ithelp@harvard.edu for assistance.

### Problem logging in to Rstudio

f you have been logged out of Rstudio (because of inactivity, for example) then you may see a login screen like this:

![rstudio-login-screen.png screenshot](images/rstudio-login-screen.png?raw=true)

To log back in to your Rstudio session, close that login page and then follow these steps:

1. Navigate to `My Interactive Sessions` in FAS OnDemand.<br/>
![Navigate-to-interactive-sessions.png screenshot](images/navigate-to-interactive-sessions.png?raw=true)

2. Re-connect to your running Rstudio session:<br/>
![Connect-to-rstudio-server screenshot](images/connect-to-rstudio-server.png?raw=true)