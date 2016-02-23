# Pombola Simple Documentation

Pombola Simple provides a platform for creating Parliamentary Monitoring sites. It's built using data from [EveryPolitician](http://everypolitician.org/).

## Creating a new site

First you'll need to create a Jekyll repository for the new site.

    $ jekyll new my_pmo_site
    $ cd my_pmo_site

## Deploying to GitHub pages

1. Follow GitHub's [instructions for creating a `gh-pages` branch](https://help.github.com/articles/creating-project-pages-manually/#create-a-gh-pages-branch).
2. Copy the `.travis.yml` and `_bin/deploy` scripts from another Pombola Simple site.
3. Create a GitHub Personal Access Token and then encrypt it with `travis encrypt GITHUB_ACCESS_TOKEN=yourtokenhere`, then replace the `secure: ` line in `.travis.yml` with the output from that command.
4. Make sure the access token has read access to public repos.
5. Make sure the person/robot who you created the access token for has push permission to the repository.
6. Push the change to GitHub
7. Done! Now every push to the `master` branch should get built on Travis and deployed to GitHub Pages.
