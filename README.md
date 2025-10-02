# Minimalist Hugo Template for Academic Websites


This repository 
This repository contains a [Hugo](https://github.com/gohugoio/hugo) template to create a personal academic website. The template uses [rosavandenende's template](https://github.com/rosavandenende/rosavandenende.github.io), but it modifies it in various ways to be more different puposes. The website is hosted on [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages).

## Illustration

The website produced by the template can be viewed at https://rayhaneh-einollahi.github.io/.


## What's Added

* A **grid layout page** that displays multiple posts across several columns.
* An **Experience page**, styled similar to LinkedIn, for showcasing professional background and achievements.


## Other Features

* The website is structured around **three main categories**: papers, courses, and data, accessible via the menu or homepage.
* **Tags (keywords)** are auto-generated to highlight covered research and teaching topics.
* An **archive page** is auto-generated to showcase the most recent additions.
* The template includes **academic-specific social icons** (e.g., office hours, Zoom, Substack, Google Scholar).
* **Metadata** beneath titles is tailored for academic use.
* The **design** (colors, fonts, spacing, buttons) is minimalist and streamlined.
* New **page archetypes** are available for papers, courses, and search.

## Installation

### On your local machine

+ Clone the repository to your local machine
+ Install [Hugo](https://gohugo.io/installation/). On a Mac, this is easily done with [Homebrew](https://brew.sh): simply run `brew install hugo` in the terminal.
+ Since the website is hosted on GitHub Pages, it is convenient to install [GitHub Desktop](https://desktop.github.com). The website can conveniently be updated from your local machine via GitHub Desktop without going to GitHub.
+ Update the `baseURL` parameter in `config.yml` with the website URL that you plan to use. By default the ULR is `https://username.github.io`.

### On your GitHub account

+ The first time that you push your repository to GitHub, you need to allow GitHub Actions and GitHub Pages so the website can be built and deployed to GitHub Pages.
+ The first step is to [ask GitHub to publish the website with a GitHub Action](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow).  GitHub offers a ready-made action to publish a Hugo website, called `Deploy Hugo site to Pages`. This action must be enabled in the [Pages Settings](https://github.com/pmichaillat/hugo-website/settings/pages) of your GitHub repository. You can view the workflow triggered by the action in the `.github/workflows/hugo.yml` file.
+ Once the GitHub Actions are enabled, GitHub will build and publish the website as soon as the repository is updated. 

## Usage

### Development

Navigate to the website directory and run `hugo server` in the terminal. The command builds the website on your machine and makes it available at http://localhost:1313. You can modify the content of the repository and develop your website entirely on your local machine.

### Compilation

Once your website is ready to be made public, run `hugo` in the terminal from the website directory. When you run the `hugo` command, Hugo processes your content, templates, and other project files and generates a static website. The resulting output is placed in the `public` folder.

### Deployment

With GitHub Desktop, commit the changes and push them to the website repository on GitHub. Then, [GitHub Actions](https://github.com/pmichaillat/hugo-website/actions/workflows/hugo.yml) build the website and deploy it to [GitHub Pages](https://github.com/pmichaillat/hugo-website/deployments/github-pages).

## License

The content of this repository is licensed under the terms of the MIT License.
