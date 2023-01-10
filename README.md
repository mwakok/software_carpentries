# Software Carpentry Lesson

[![CC BY 4.0][cc-by-shield]][cc-by]

## Content
Collection of materials to host a Software Carpentries workshop. These materials are adaptations from the lessons provided by the [Software Carpentry](https://software-carpentry.org/lessons/)

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
- [Python lesson plan](/lesson_plans/2022_10_17_Python.md)
- [Status of repository at time of workshop]

## Tools
For online teaching, I use the following tools

- [Git and Gitbash](https://gitforwindows.org/)

- Python installation with [Anaconda](https://www.anaconda.com/products/distribution#download-section)

- Windows Terminal Preview with [split screen](https://endjin.com/blog/2020/05/5-tips-for-an-awesome-windows-terminal-experience) to show the [terminal history](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md). 

- [Gitautopush](https://pypi.org/project/gitautopush/) to upload the notebooks to a GitHub repository during the workshop for reference. This setup requires a passsword-less ssh key. For more details, see below.

- [Windock](https://www.ivanyu.ca/windock) for quickly managing the position, aspect ratio, and size of my windows. 

- For plenary exercises, I use [polls for Zoom](https://www.howtogeek.com/674907/how-to-create-polls-in-zoom-meetings/)

- To control my webcam background, I pipe a virtual webcam from [XSplit VCam](https://www.xsplit.com/vcam) into [OBS](https://obsproject.com/), ensuring consistent backgrounds across various online meeting programs (Teams, Zoom, Skype) 

### Setup gitautopush
During the workshop, I want to provide a link to a copy of notebooks I develop as part of hands-on teaching. This allows the participants to look up past commands and quickly rejoin the session after getting stuck, without having access to all the lesson material. The most practial solution I settled on is [gitautopush](https://pypi.org/project/gitautopush/). `gitautopush` lets you automatically track the latest changes to a git repository, and automatically push them to GitHub. You can then ask the particiapants to visit the GitHub url with the notebook, and they will be able to see any changes that you've made.

**Steps**
1. Create a passwordless ssh-key for github. Create a new rsa ssh-key called `id_rsa_open` (leave password empty), add the key to GitHub, and then add the following lines to `./ssh/config`:

    ```
    Host github.com
        HostName github.com
        IdentityFile ~/.ssh/id_rsa_open
    ```

2. Install `gitautopush` in the conda environment you use for teaching.

3. Create a new branch in the repository you want to upload the changes to. In my case, I use a `notes` branch in the repository that contains the [learner materials](https://github.com/mwakok/software_carpentry_learner).

4. Run gitautopush in the local (git) folder you will use for teaching with `gitautopush .`. Minimize the terminal to run it in the background.

## License

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
