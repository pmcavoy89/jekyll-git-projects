# jekyll-git-projects
List your GitHub repositories that use GitHub Pages on your Jekyll site or GitHub Pages base site.

## Goal
My website is a Jekyll site and I use GitHub for projects to teach development. I plan on releasing the code on the master branch of the projects and the `/docs` for GitHub Pages to be the tutorial of those projects.

This is a [Jekyll Generator](https://jekyllrb.com/docs/plugins/generators/) that creates a page on your site to list all your GitHub repositories with GitHub Pages enabled and provides a link to them. 

## How it Works
The plugin takes a [personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) from your GitHub account to authenticate with the [GitHub API](https://docs.github.com/en/rest). 

> ***Note***: Please only use the scope of `public_repo` for your personal access token. The generator is designed to only read your public repositories and will not modify them.

Then it will run to get the authenticated user's repository using the GitHub API. Documentation found [here](https://docs.github.com/en/rest/reference/repos#list-repositories-for-the-authenticated-user). If the repository does not have the `homepage` set, then it'll check for the `has_pages`. Given the repository meets those requirements, a following call of to grab the [pages information](https://docs.github.com/en/rest/reference/repos#get-a-github-pages-site) will be made.

### API Definition
* `name` from GitHub API response is the `title` of the card
* `description` from GitHub API response is the `subtitle` of the card
* `html_url` from GitHub API response is the `href` of the card

> **Note**: Future release will grab an image from the repository to be part of the card
