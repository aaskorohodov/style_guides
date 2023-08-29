# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Politics](#politics)
* [Format](#format)
* [Catalogue](#catalogue)
* [Structure](#structure)
  * [Brief project's description](#brief-projects-description)
  * [Table of contents for readme](#table-of-contents-for-readme)
  * [Installation](#installation)
  * [Configuration](#configuration)
  * [Usage](#usage)
  * [Project structure](#project-structure)
* [Tips](#tips)
<!-- TOC -->

# Politics

Every project should have readme.md file for Developers. If some project requires readme.md for Users - you can 
include one as well, mentioning in its name, that it is designed for Users (e.g. 'readme_user.md').

In general, there should be no questions about 'how to launch this thing?' after reading your readme.md.

# Format

<p align="center">
  <img src="media/readme/markdown.svg.png" 
      width="30%"
      height="30%"
      style="background-color:grey;
             border: 2px solid grey;
             border-radius: 16px;">
</p>

Markdown (.md) is the format, that should be used for any project, when writing it for Users or Developers.

[You can read more about it here.](https://www.markdownguide.org/basic-syntax/)

# Catalogue

readme.md should be in the root-folder of your project. This way it will be accessible for different applications 
like GitHub to be displayed on the home page of your project.

If there is a need in placing some files to support your readme.md (e.g. pictures), you should create a folder '.doc'
in the root-folder of your project and place any related files there.

# Structure

Readme should include:

- [Brief project's description (overview)](#brief-projects-description)
- [Table of contents for readme (if readme is long enough)](#table-of-contents-for-readme)
- [Installation (how, what, in which order to install)](#installation)
- [Configuration (if required, e.g. setting .env, requisites, etc.)](#configuration)
- [Usage (what to do, when project is launched)](#usage)
- [Project structure](#project-structure)
- readme should be structured, using Headers and sub-headers (#, ##, ###, ...)

In some cases, there is no need to include all of these articles in a readme-file. For example, this exact repository's
readme combines installation, configuration and usage under single header.

## Brief project's description

Project description should let any User/Developer to quickly get sense of what this project is about. It should be 
concise and provide a high-level overview of what the project does. It should capture the essence of your 
project **in just a few sentences**.

* Place project's name in some visible spot
* Describe on top-level, what this project does
* Is this project is a part of a bigger application - mention where it related to

## Table of contents for readme

If your readme is big enough, you should consider adding table of contents, to make navigation easier. To do that,
using PyCharm, you can:

> Press L-Alt+Insert
>> Select 'Table of contents'

## Installation

Installation guide should be as complete as possible. It should include all the possible commands, steps, bumps and
errors, that potential User may face.

* Write it for a person, who does not know anything about programming at all
* Add section, that includes instruction about launching development environment
* Add section, that describes launching project in product environment

For example:

> 1. Open up a terminal using Ubuntu 22.1 or later
>   1. Press Win+A to open menu
>   2. In the search-bar start typing 'Terminal', select Terminal application
>   3. Alternatively, you can press RMB to open context-menu and select 'Terminal', from desired folder
>      1. In this case, your terminal will appear right in the folder, where you need it
> 2. In the terminal, navigate to the root-folder with the project
>    1. To move 1 catalogue up, use 'cd..' - type it in terminal and press 'Enter'
>    2. ...

You may assume that any Developer after you will be at least at your level, so there is no need to be so detailed,
but this may not be true. There might be a case, in which you will get sick, and your work will be picked up by
someone, who appeared to have the privileges to download your project's repository, while having 0 skills in 
working with your instruments.

## Configuration

Configuration should include any parameter, that User may need to launch your Project in developer or production
environment. This may include:

- Any DB requisites
- Any settings in your Project's files
- Any environmental variables, including describing the way itself, how to set them, if necessary
- Describe any files with environmental variables
- Describe how to change file with env or envs themselves
- Describe all the possible command-line flags and options, that User may need to reconfigure Project
- etc.

Try to write your configuration instruction, from the perspective of a non-programmer, who needs to launch your
project, while all the DBs, file-systems or any other infrastructure collapsed. This User may need to change all
the requisites to some new ones, pull yur Project to the new Server and generally start it from scratch, without
any of your support.

## Usage

This section should illustrate briefly, what Users and Developers may do with your Application, when it is launched.
This may include:

- Scenarios of usage
- Possible configuration or setting of the already running application
- Implicit features and any use-case, that may not be obvious

## Project structure

This section should include complete description of how this project is structured. This section should not only 
help Users/Developers to navigate inside your project, but as well show, where and how to add any possible changes,
to follow your structural design.

This section should not only explain the catalogue structure, but the structural units of your code itself. These
can be you interfaces, base-classes and modules, their main purpose and idea. There should not be too deep 
description of each unit, but a general guide, that can help start making changes or adding new functionality.

If there are any default files and folders, that are made in coherence with these guidelines, there is no need to 
include them in your readme, as they are the same for each repository. For example:

- What is '.gitignore'
- What is '.doc' folder
- What are these strange 'requirements.txt'
- What is a 'media' folder about
- etc.

# Tips

- To create table of contents in PyCharm, use Alt+Insert.
- To update table of contents, use PyCharm's context actions
- Different md-redactors support different markdown. Consider using some of the most popular standards (e.g. GitHub)
- You can modify your readme.md and other files, using PyCharm or any online services