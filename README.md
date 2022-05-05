# DevOps project

This repository has been created for the Fall 2021 edition of course [CS-EJ4104 Introduction to Devops](https://sisu.aalto.fi/student/courseunit/aalto-OPINKOHD-1143602494-20210801/brochure). For additional information about the project, visit the [related MyCourses page](https://mycourses.aalto.fi/course/view.php?id=34305&section=3).

The goal of the project was to create a personal website. Instead of using the built-in website generator in GitHub Pages, we had to use a third-party tool: Hugo, a framework for building static websites that takes Markdown documents as input and produces HTML files as output. We also had to configure a continuous delivery pipeline through GitHub Actions to trigger a build and (if that is successful) publish the site on GitHub Pages. The workflow file implemented can be found at [.github/workflows/deploy-worflow.yml](.github/workflows/deploy-worflow.yml)

For the project, we used the GitHub repository that was created through the form on A+. The repository is created under Aalto organization owned on GitHub: it is private and the course staff has access to it.

Two branches in the git repository were required for this project: the master branch for the source (Markdown) files used by Hugo, and the gh-pages branch to publish the site. We built and deployed the website on GitHub Pages through GitHub Actions. It is not enough to build and deploy the site some other way (for instance, manually from your local machine) to fulfill the project requirements.