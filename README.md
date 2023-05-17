# Software Carpentry Lesson

[![CC BY 4.0][cc-by-shield]][cc-by]

## Content
Collection of materials to host a Software Carpentries workshop. These materials are adaptations from the lessons provided by the [Software Carpentry](https://software-carpentry.org/lessons/).

The data and exercises for participants are provided in a separate repository: https://github.com/mwakok/software_carpentry_learner and should be cloned or downloaded as a zipfile prior to the workshop. They will create all further materials in the local directory of the repository.

I am currently exploring the useability of [Jupyterlite](https://jupyterlite.readthedocs.io/en/latest/) either as a backup environment for participants who encounter issues with their own installation or as general workshop environment. The workshop materials can be executed through the [Jupyterlite instance](https://mwakok.github.io/software_carpentries/lab/index.html) running in this repository.

## Feedback
Feel free to use these materials and I welcome any feedback (mistakes, suggestions) in the form of an issue.

## Workshops

### Nov 2021 

- Workshop [homepage](https://4turesearchdata-carpentries.github.io/2021-11-15-tudelft-online/)
- [Python lesson plan](/lesson_plans/2021_11_15_Python.md)
- [Status of repository at time of workshop](https://github.com/mwakok/software_carpentries/tree/0.0.1)

### Oct 2022

- Workshop [homepage](https://4turesearchdata-carpentries.github.io/2022-10-17-tudelft-online/)
- Python lesson plan [day 1](/lesson_plans/2022_10_17_Python1.md) [day 2](/lesson_plans/2022_10_18_Python2.md)
- [Status of repository at time of workshop]

## Tools
For online teaching, I use the following tools

- [Git and Gitbash](https://gitforwindows.org/)

- Python installation with [Anaconda](https://www.anaconda.com/products/distribution#download-section)

- Windows Terminal Preview with [split screen](https://endjin.com/blog/2020/05/5-tips-for-an-awesome-windows-terminal-experience) 

- Display the [terminal history](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md). For compatibility with `gitautopush`, see the [instructions below](#sharing-terminal-history-with-gitautopush). For easy management of the two terminals, I use the (horizontal) split window feature of Windows Terminal Preview.

- [Gitautopush](https://pypi.org/project/gitautopush/) to upload the notebooks to a GitHub repository during the workshop for reference. This setup requires a passsword-less ssh key. For more details, see below.

- [Windock](https://www.ivanyu.ca/windock) for quickly managing the position, aspect ratio, and size of my windows for screen sharing in online teaching. 

- For plenary exercises, I use [polls for Zoom](https://www.howtogeek.com/674907/how-to-create-polls-in-zoom-meetings/)

- To control my webcam background, I pipe a virtual webcam from [XSplit VCam](https://www.xsplit.com/vcam) into [OBS](https://obsproject.com/), ensuring consistent backgrounds across various online meeting programs (Teams, Zoom, Skype) 

### Set up gitautopush
During the workshop, I want to provide a link to a copy of the notebooks I develop as part of hands-on teaching. This allows the participants to look up past commands and quickly rejoin the session after getting stuck, without needing to access all the lesson materials. The most practial solution I settled on is using [gitautopush](https://pypi.org/project/gitautopush/). `gitautopush` lets you automatically commit and push the latest changes in a git repository to GitHub. By letting `gitautopush` track the changes I make in the lesson notebooks, they are progressively made available in a GitHub repository at a defined interval (default is 10 seconds). You can then ask the participants to visit the GitHub url with the notebook, and they will be able to see the latest version of your notebook. Participants will need to refresh the webpage to see the latest changes.

**Steps**
1. Install `gitautopush` with `pip install gitautopush`. As I use a conda environment for the Python lesson, I recommend installing the package in the conda environment you use for teaching.

2. `gitautopush` requires permission to push to your GitHub repository. A password-protected ssh key will ask for a password for each push, stalling the automated push. Two possible solutions are:

    - **(Recommended)** Use an [ssh-agent for a single sign-on](https://www.ssh.com/academy/ssh/agent). In a terminal, start the ssh-agent with

        ```
        eval `ssh-agent` 
        ``` 

        Then, run 
        
        ```
        ssh-add ~/.ssh/id_rsa
        ``` 

        to add the `id_rsa` private key (replace ssh-key name for other keys if needed). You will get prompted for your password, and after providing this, no further password prompts are required for the provided key **during this terminal session**.

    - **(If all else fails)** You can create a passwordless ssh-key for GitHub. Create a new rsa ssh-key called `id_rsa_open`, leaving the passwork blank, and [add the key to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). Then, configure ssh to use this IdentityFile by adding the following lines to `./ssh/config` (create the file if it doesn't exist yet):

        ```
        Host github
            HostName github.com
            IdentityFile ~/.ssh/id_rsa_open
        ```

        As password-less ssh-keys are a security risk, make sure to change the IdentityFile to your regular ssh-key.

3. Either create a new repository (local and online) or create a new branch in the repository you want to upload the changes to. In my case, I use a `notes` branch in the repository that contains the [learner materials](https://github.com/mwakok/software_carpentry_learner). Note that `gitautopush` requires that the repository has at least a single previous push. 

4. In the same terminal you set up the ssh-agent, run `gitautopush` in the local (git) folder you will use for teaching by executing  

    ```
    gitautopush .
    ```
    Minimize the terminal to run it in the background. For more details, visit the [gitautopush documentation](https://github.com/choldgraf/gitautopush).

### Sharing terminal history with gitautopush
If your lesson requires you to upload your executed terminal commands with gitautopush, we will need to adjust the settings for [displaying the terminal history](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md). Credits go to [Giordano Lipari (@wmotion)](https://github.com/wmotion) for this solution.

1. Follow steps 1-2 in the [gitautopush setup](#set-up-gitautopush).
2. Create a new git repository separate from your working directory and create the file `command_history.txt`. We will pipe your command history to this file.
3. Commit and push your (empty) file to a GitHub repository.
4. Next, we will set up your two terminals to [display the command history](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md). In a **new(!)** terminal, set up your terminal to store the each command in the history by executing

    ```{bash}
    export PROMPT_COMMAND="history -a;$PROMPT_COMMAND"
    ```

    Then, in a second terminal (or horizontal terminal split in Windows Terminal Preview), execute

    ```    
    FILE="<path-to-command_history.txt>"
    tail -n 0 -f ~/.bash_history | tee $FILE
    ```

    In addition to displaying the command history, all commands will be written to `command_history.txt`. If needed, you can use `tee -a $FILE` to append to `command_history.txt` instead of overwriting the file. 

5. Start `gitautopush` in the repository containing `command_history.txt`. Ensure that you have enabled the ssh-agent for single sign-on. You can now commit and push all changes to the command history to your GitHub repository.

## License
This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
