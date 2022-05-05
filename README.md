# Personal website based on Hugo framework and built with Github actions

This repository is a modified version of the project that has been created for the Fall 2021 edition of course [CS-EJ4104 Introduction to Devops](https://sisu.aalto.fi/student/courseunit/aalto-OPINKOHD-1143602494-20210801/brochure). For additional information about the project, visit the [related MyCourses page](https://mycourses.aalto.fi/course/view.php?id=34305&section=3).

The goal of the project was to create a personal website. Instead of using the built-in website generator in GitHub Pages, we had to use a third-party tool: Hugo, a framework for building static websites that takes Markdown documents as input and produces HTML files as output. We also had to configure a continuous delivery pipeline through GitHub Actions to trigger a build and (if that is successful) publish the site on GitHub Pages. The workflow file implemented can be found at [.github/workflows/deploy-worflow.yml](.github/workflows/deploy-worflow.yml)

The original project repository is owned by the course staff and is private, therefore the project contents were moved to own repo and adjusted for personal use. 

Two branches in the git repository were required for this project: the master branch for the source (Markdown) files used by Hugo, and the gh-pages branch to publish the site. We built and deployed the website on GitHub Pages through GitHub Actions. 