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

This case study provides instructions for following along using either **Docker Desktop** or **Docker through a Command Line Interface (CLI)**. If you are comfortable working with a command line interface, you should still install Docker Desktop as it efficiently provides all of the necessary components to use Docker through a CLI. However, you do not need to use Docker Desktop after installing it. Note that you can still use a command line within Docker Desktop, and the application provides additional tools, documentation, and an [AI assistant, Gordon](https://docs.docker.com/ai/gordon/). 

However, if you are a beginner, or largely uncomfortable working with a command line interface, it is recommended that you follow along with this case study using Docker Desktop.

To use Docker Desktop, you will need the following installed:

* Docker Desktop (install [for Windows](https://docs.docker.com/desktop/setup/install/windows-install/), [for Mac](https://docs.docker.com/desktop/setup/install/mac-install/), or [for Linux](https://docs.docker.com/desktop/setup/install/linux/))
* Notepad, Sublime, Visual Studio Code or another **text editor**

To use Docker through a CLI, you will need the following installed:

* **Docker Engine**
* **Docker CLI**
* Have access to and familiarity with a local command line interface (CLI)
* Notepad, Sublime, Visual Studio Code, nano, vim, or another **text editor**

Both the Docker Engine and Docker CLI are provided through Docker Desktop. So even if you do not want to use Docker Desktop, and instead want to use Docker through a CLI, please install Docker Desktop [for Windows](https://docs.docker.com/desktop/setup/install/windows-install/), [for Mac](https://docs.docker.com/desktop/setup/install/mac-install/), or [for Linux](https://docs.docker.com/desktop/setup/install/linux/)

<u>It will also be helpful to be have the following skills:</u>

* ability to navigate file systems. Please use or review the [Software Carpentry "Navigating Files and Directories" tutorial](https://swcarpentry.github.io/shell-novice/02-filedir.html) if needed.
* basic R skills (many introductory courses can be found online, including [this one](https://hutchdatascience.org/Intro_to_R/))
* familiarity with dplyr and ggplot2, or willingness to learn (these [dplyr](https://rstudio.github.io/cheatsheets/data-transformation.pdf) and [ggplot2](https://rstudio.github.io/cheatsheets/data-visualization.pdf) cheatsheets may be helpful, as well as the original [open case studies](https://www.opencasestudies.org/search.html))


<u>For optional, more extensive reproducibility activities, you will need the following:</u>


* minimal Git and GitHub knowledge or experience (see [this related case study](https://www.opencasestudies.org/ocs-bio-version-control/) for necessary skills)
* a **GitHub account** (see [here to signup](https://github.com/signup))

### Target Audience

The target audience for this case study is scientists and researchers who 

* work on analyses within collaborative teams 
* use software that may be updated frequently or have several necessary dependencies in order to install
* want to create more reproducible analyses
* do not yet use containers or want to get more comfortable with modifying what is available in a container.

### Motivation

This case study introduces the use of containers in the context of a realistic collaborative scientific project. 
Learners will use a pre-existing Docker container to run an analysis of metadata from a curated data resource with microbiome and metabolome data. 
This case study introduces containers as a tool for increasing the reproducibility of a scientific analysis within a team project, describing why and how to use them to standardize computing environments.
Additional topics that will be covered include how to find and share container images, how to mount a volume of analysis scripts, and how to explore output and save results from an analysis performed in a container.

### Main Questions

The main questions in this case study are the following:

1. How does one use containers to improve the reproducibility of their work? (Are containers always necessary?)
1. How does one use a container and modify a container?
1. What are microbiome and metabolome data and how can they be used together?

### Learning Objectives

The learning objectives of this case study are the following:

<u>**Data Science Learning Objectives**</u>

1. Discuss ways in which containerization promotes reproducibility within collaborative scientific research.
1. Describe how containerization is one of several tools to increase the reproducibility of scientific research.
1. Employ multiple reproducibility best practices together within the context of containerization (e.g., mounting a volume of version-controlled scripts, sharing a container image).
1. Evaluate what should or should not be included in a container.
1. Identify contexts where containerization (potentially with Docker) is not appropriate or needed.
1. Practice the containerization process to reproduce, extend, and share a data analysis and its results.
1. Verify that results or outputs (e.g., messages in logs from analyses run in containers) match expectations.

<u>**Statistical Learning Objectives**</u>

1. Explain how statistical power is impacted by the number of samples in an analysis.
1. Recognize the need and considerations for data harmonization when utilizing multiple data sources.
1. Describe how the number of observed metabolites is impacted by the number of samples in a dataset.

<u>**Biological/Bioinformatics Objectives:**</u>

1. List the value and potential applications of Data collection or resource.
1. Explain the limitations and cautions associated with using a data collection or curated data resource for your own work.
1. Relate the utility of pairing microbiome and metabolome data for biological research.
1. Build visualizations to communicate the relationship among variables in a table.

### Context 

The metabolome is a collection of metabolites or low-molecular weight organic (containing carbon-hydrogen bonds) molecules found in a specific sample or organism.
The microbiome is the set or collection of microorganisms (e.g., bacteria, viruses, fungi, etc.) that live in a particular environment such as the human gut. 
Sequencing the microbiome can help us to identify what bacteria and other microorganisms are present in the human gut, which can have an impact on human health.
However, to actually see the activity of or impact caused by the presence of those microorganisms, the identification of metabolites in the samples are helpful.
Studies will often pair microbiome and metabolome data for a greater depth of scientific insight and conclusions.

A curated data resource is a collection of datasets that have been gathered or curated by a group for secondary use within the scientific field. 
In this case study, we work with a [curated data resource introduced by Muller, Algavi, and Borenstein (2022)](https://www.nature.com/articles/s41522-022-00345-5). 

Different researchers, especially those located at different institutions, those at different career stages, and those who have different research focuses have different computing environments (potentially differences in operating systems, software, software versions, etc.).
The differences between computers can be problematic for performing and sharing reproducible research.
A container is often used to standardize the computing environment within a team by providing a standardized computing environment for everyone using it. 

### Introduction to Containers

This section introduces the learner to many components of the containerization process, and explores when and why to use containers.

Dockerfiles are text-based scripts that contain commands defining how an image will be built. 
A Dockerfile serves as a blueprint or the starting point of the containerization process. 
Dockerfiles are built to produce images. 
Images are frozen, layered snapshots of what the container will be, containing the files for the system libraries. 
Images are much larger than Dockerfiles and less readable. 
They are the most common way to share a container and are often stored in registries (like Docker Hub). 
Images are run to create containers and file systems or volumes may be mounted during the run process so that isolated containers have access to scripts or data. 
Any updates made to files (i.e., data or scripts) from the mounted volume within the container persist to your local file system once the container is no longer running.

Containers are useful for standardizing the computing environment within a team or between different machines (e.g., local laptop and institutional HPC or cloud computing environment).
While containers are not always necessary, they are especially useful if a collaborative team is working on a large analysis and if software has many dependencies. 
This case study focuses on using an existing container to support an analysis. 
In the case study, the learner will use Docker to work with containers, through either Docker Desktop or through a command line interface. 

### What are the Data? 

The data used in the case study come from Table 1 in [this paper](https://www.nature.com/articles/s41522-022-00345-5) by Muller, Algavi, and Borenstein (2022). 
Table 1 describes the curated gut microbiome-metabolome datasets that this study aggregated in order to curate a resource for the research community. 

The variables that are used in the case study include: 

Variable   | Details
---------- |-------------
**`dataset_name`**  | A character/string identifying the dataset (often containing author, studied illness, and year of the study).
**`num_paired_samples`**  | The number of samples within the dataset that have paired fecal microbiome-metabolome data.
**`longitudinal`** | A character/string reporting whether that dataset has longitudinal data ("Yes" or "No").
**`hmdb_annotated_compounds`** | The number of metabolites that were identified within that dataset and annotated with the Human Metabolome Database (HMDB) [@Wishart_etal_2009].
**`kegg_annotated_compounds`** | The number of metabolites that were identified within that dataset and annotated with Kyoto Encyclopedia of Genes and Genomes (KEGG) [@Kanehisa_Goto_2000; @Kanehisa_etal_2025].

### Limitations

This section describes limitations of this case study, including the scope of the use of containers in the case study and the scope of the data analysis, when Docker is not an appropriate tool, and limitations of curated data resources. 

### Ethical Considerations

This section lists several ethical considerations of working with containers, including considerations for using containers with clinical and health data (never including PII or PHI in a container image), considerations for work in large collaborative teams, and considerations for using secondary data.

### Packages and Setup

R packages used in this case study include the following: 

Package    | Use
---------- |-------------
[here](https://cran.r-project.org/web/packages/here/refman/here.html){target="_blank"} | Constructs paths within project
[tabulapdf](https://cran.r-project.org/web/packages/tabulapdf/refman/tabulapdf.html){target="_blank"}      | Extract data from a PDF
[readr](https://cran.r-project.org/web/packages/readr/refman/readr.html){target="_blank"} | Read and write rectangular data (like `.csv`, `.tsv`, etc.)
[tidyverse](https://cran.r-project.org/web/packages/tidyverse/refman/tidyverse.html){target="_blank"} | Data wrangling
[ggplot2](https://cran.r-project.org/web/packages/ggplot2/refman/ggplot2.html){target="_blank"}      | Visualize data
[patchwork](https://cran.r-project.org/web/packages/patchwork/refman/patchwork.html){target="_blank"} | Combining multiple plots

This section also describes the structure of the next several sections, which each involve activities related to configuring the container, as well as activities related to using the container for an analysis.

### Data Import 

In this section, the learner will pull a Docker image from Docker Hub and run the image in order to create the container. 
The learner will run a script within the container to extract the data used in this case study from a PDF. 

### Data Exploration

In this section, the learner will inspect the Dockerfile that is used to create the image and container used in the case study. 
They will also inspect the data imported in the previous section, to determine what data wrangling will be necessary. 

### Data Wrangling

In this section, the learner will run a script to wrangle the data into a format that can be used more easily for visualization and analysis.
Additionally, they will add a package to the Dockerfile.

### Data Visualization 

In this section, the learner will build a new image from the modified Dockerfile, and run that image to create a container that includes the additional package.
They will also run a visualization script to create scatterplots to compare the number of annotated compounds to the number of samples with paired data in the curated data resource.

### Data Analysis

In this section, the learner will run a script to calculate correlations between the number of annotated compounds and the number of samples in the datasets included in the curated data resource.
After completing the analysis, they will stop and delete the container. 
They will also learn about how to share scripts and Dockerfiles or images with collaborators. 

### Summary

This section summarizes the case study, describing the "Dockerfile -(build)-> image -(mount and run)-> container" process. 
It also provides a reminder of the steps that the learner took throughout the case study. 
It includes a process and decision points image, which emphasizes the decisions that are made throughout the containerization process. 
It also includes a summary plot, which reminds the learner of the motivation for using containers as part of a reproducible and collaborative scientific project.

### Troubleshooting Containers

This section describes resources that can be helpful for troubleshooting issues with containers, and provides considerations for using AI with containers.

### Continued Learning

This section provides exercises for the learner to keep practicing their container skills and to learn new ones. 
These include adding another package to the container used in the case study, editing the Dockerfile to run additional scripts, creating a Dockerfile from scratch to run a similar analysis with Python, and using GitHub actions to use a container.

### Helpful links and resources

* [ITN Containers for Scientists course](https://hutchdatascience.org/ITN_course_search/Containers_for_Scientists_coursePage.html)
* [ITN Making Science Reproducible - A Capstone Project Course](https://hutchdatascience.org/ITN_course_search/reproducibility_capstone_coursePage.html)
* [Docker Documentation](https://docs.docker.com/)
* [Docker 101 Tutorial](https://www.docker.com/101-tutorial/)
* [Gordon AI](https://docs.docker.com/ai/gordon/)
* [Podman](https://docs.podman.io/en/latest/)
* [Singularity / Apptainer](https://docs.sylabs.io/guides/latest/user-guide/)
* For a discussion on security vulnerabilities, especially for images, see [this paper](https://academic.oup.com/gigascience/article/10/6/giab025/6291571) by Kaur, Dugré, Hannah, and Glatard (2021).


