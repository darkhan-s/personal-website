---
title                 : "DevOps"
disableTitleSeparator : true
---

My name is Saidnassimov Darkhan and I am a second year Master's student in Automation and Electrical Engineering at Aalto University. This is the website for the "Introduction to DevOps" course final project. [^1] The project utilizes Hugo to build a static website using markdown files and Github Actions to automate deployment. To know more about the project goals and methods, check the following [chapter](#this-project-explained). To hear more about why I chose to study DevOps, check out [why I am interested in DevOps](posts/whydevops) or from the navigation panel. If you want to know more about me or to contact me, check out a page [about me](who/).

## What is DevOps

> *"DevOps is the combination of cultural philosophies, practices, and tools that increases an organization’s ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes. This speed enables organizations to better serve their customers and compete more effectively in the market."*
>
> **— Amazon**[^4]


## This project explained

The goal of the project is to create a personal website. Instead of using the built-in website generator in GitHub Pages, we have to use a third-party tool: Hugo, a framework for building static websites that takes Markdown documents as input and produces HTML files as output. We also need to configure a continuous delivery pipeline through GitHub Actions to trigger a build and (if that is successful) publish the site on GitHub Pages. The workflow file implemented can be found at the [Codebase](posts/codebase/)

For the project, we must use the GitHub repository that needs to be created through the form on A+. The repository is created under Aalto organization owned on GitHub: it is private and the course staff has access to it.

Two branches in the git repository are required for this project: the master branch for the source (Markdown) files used by Hugo, and the gh-pages branch to publish the site. We must build and deploy the website on GitHub Pages through GitHub Actions. It is not enough to build and deploy the site some other way (for instance, manually from your local machine) to fulfill the project requirements.

Requirements list
---|:---:
Website is generated by Hugo|:thumbsup:
Deployment utilizes Github Actions|:thumbsup:
Deployment is done on gh-pages branch|:thumbsup:
3 pages minimum|:thumbsup:
Landing page with 100 words starting with DevOps|:thumbsup:
Links at the landing page|:thumbsup:
Static page at /who with 100 words|:thumbsup:
An image with 250px minimum|:thumbsup:
Blog post with "Why..DevOps" in heading|:thumbsup:
Unordered list with 250-500 words|:thumbsup:


[^1]: [My Courses](https://mycourses.aalto.fi/course/view.php?id=34305)
[^2]: [Static page](who/)
[^3]: [Why I am interested in DevOps](posts/whydevops)
[^4]: [What is DevOps?](https://aws.amazon.com/devops/what-is-devops/)