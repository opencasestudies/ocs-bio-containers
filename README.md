# Biomedical Open Case Studies: Using containers for collaborative, reproducible research

### Useful Links

-   HTML: <https://www.opencasestudies.org/ocs-bio-containers/>
-   GitHub:
    <https://github.com/opencasestudies/ocs-bio-containers>

### Disclaimer

The purpose of the [Open Case
Studies](https://opencasestudies.github.io) project is **to demonstrate
the use of various data science methods, tools, and software in the
context of messy, real-world data**. A given case study does not cover all 
aspects of the research process, is not claiming to be the most appropriate 
way to analyze a given data set, and should not be used in the context of 
making policy or clinical decisions without external consultation from scientific 
experts or medical care professionals. In addition, due to size constraints, 
datasets used within a case study may be a subset of the original/full dataset.

### License

This work is licensed under the Creative Commons Attribution-NonCommercial 4.0 [(CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/deed.en) United States License unless otherwise noted.

### Citation

To cite this case study:

Isaac, Kathryn J and Teichman, Sarah, and Thomas, Oshane O and Hoffman, Ava M and Wright, Carrie. (2026). [https://github.com/opencasestudies/ocs-bio-containers/](https://github.com/opencasestudies/ocs-bio-containers). Using containers for collaborative, reproducible research (Version v1.0.0).

### Funding

This work is funded through the National Institutes of Health, specifically the National Institute of General Medical Sciences: Grant Number 1R25GM160622.

### Acknowledgments

We would like to acknowledge [Candace Savonen](https://www.cansavvy.com), [Casey Greene](https://greenelab.com/members/casey-greene.html), [Emma Lathouwers](https://greenelab.com/members/emma-lathouwers.html), [Jeff Leek](https://jtleek.com), and ethicist [Jodyn Platt](https://medschool.umich.edu/profile/3774/jodyn-platt) for their expert review of this case study.

Icons are from [iconpacks](https://www.iconpacks.net/).

Avatars are from [avataaars](https://getavataaars.com/).

### Title

Using containers for collaborative, reproducible research

### Prerequisites

:::{.prereq_box}
::::{.prereq_box_header}
Prerequisites
::::
::::{.inner_block}

This case study provides instructions for following along using either **Docker Desktop** or **Docker through a Command Line Interface (CLI)**. If you are comfortable working with a command line interface, you do not need to install/use Docker Desktop. Note that you can still use command line within Docker Desktop and the application provides additional tools, documentation, and an [AI assistant, Gordon](https://docs.docker.com/ai/gordon/). 

However, if you are a beginner, or largely uncomfortable working with a command line interface, it is recommended that you follow along with this case study using Docker Desktop.

Throughout the case study, a tab structure will be used. By default instructions for using Docker Desktop will be shown. Click the "Docker through a CLI" tabs if you would prefer not to use Docker Desktop. Installation instructions are provided using this tab structure as well.

:::{.panel-tabset}

### Docker Desktop

You will need the following installed:

* Docker Desktop (install [for Windows](https://docs.docker.com/desktop/setup/install/windows-install/), [for Mac](https://docs.docker.com/desktop/setup/install/mac-install/), or [for Linux](https://docs.docker.com/desktop/setup/install/linux/))
* Notepad, Sublime, Visual Studio Code or another **text editor**

### Docker through a CLI

To follow along with this case study, you’ll need the following installed:

* **Docker Engine**
* **Docker CLI**
* Have access to and familiarity with a local command line interface (CLI)
* Notepad, Sublime, Visual Studio Code, nano, vim, or another **text editor**

Both the Docker Engine and Docker CLI are provided through Docker Desktop. So even if you do not want to use Docker Desktop, and instead want to use Docker through a CLI, please install Docker Desktop [for Windows](https://docs.docker.com/desktop/setup/install/windows-install/), [for Mac](https://docs.docker.com/desktop/setup/install/mac-install/), or [for Linux](https://docs.docker.com/desktop/setup/install/linux/)

:::

<u>It will also be helpful to be have the following skills:</u>

* ability to navigate file systems. Please use or review the [Software Carpentry "Navigating Files and Directories" tutorial](https://swcarpentry.github.io/shell-novice/02-filedir.html) if needed.
* basic R skills (many introductory courses can be found online, including [this one](https://hutchdatascience.org/Intro_to_R/))
* familiarity with dplyr and ggplot2, or willingness to learn (these [dplyr](https://rstudio.github.io/cheatsheets/data-transformation.pdf) and [ggplot2](https://rstudio.github.io/cheatsheets/data-visualization.pdf) cheatsheets may be helpful, as well as the original [open case studies](https://www.opencasestudies.org/search.html))


<u>For optional, more extensive reproducibility activities, you will need the following:</u>


* minimal Git and GitHub knowledge or experience (see [this related case study](https://www.opencasestudies.org/ocs-bio-version-control/) for necessary skills)
* a **GitHub account** (see [here to signup](https://github.com/signup))

