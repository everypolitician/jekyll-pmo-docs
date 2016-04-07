# TheyWorkForYou Documentation

TheyWorkForYou is an approach to creating Parliamentary Monitoring sites.

This involves combining data from [EveryPolitician](http://everypolitician.org/) with other site-specific sources, and automatically rebuilding a static site (stored in the `gh-pages` branch of the site’s repo, for deployment to [Github Pages](https://pages.github.com/)) when any of the underlying information changes. Almost all functionality is provided through Jekyll plugins, using Travis to rebuild the site on request.

## Creating a new site

First you'll need to create a Jekyll repository for the new site.

    $ jekyll new my_pmo_site
    $ cd my_pmo_site

## Deploying to GitHub pages

1. Follow GitHub's [instructions for creating a `gh-pages` branch](https://help.github.com/articles/creating-project-pages-manually/#create-a-gh-pages-branch).
2. Enable Travis CI builds on the repository with `travis enable`.
3. Copy the [`.travis.yml`](https://github.com/theyworkforyou/shineyoureye/blob/4bef61e3e8e1275db73a4e5c13037162d6dfd710/.travis.yml) and [`_bin/deploy`](https://github.com/theyworkforyou/shineyoureye/blob/4bef61e3e8e1275db73a4e5c13037162d6dfd710/_bin/deploy) scripts from another site built using this approach, e.g. [shineyoureye](https://github.com/theyworkforyou/shineyoureye).
4. Create a GitHub Personal Access Token and then encrypt it with `travis encrypt GITHUB_ACCESS_TOKEN=yourtokenhere`, then replace the `secure: ` line in `.travis.yml` with the output from that command.
5. Make sure the access token has read access to public repos.
6. Make sure the person/robot who you created the access token for has push permission to the repository.
7. Push the change to GitHub
8. Done! Now every push to the `master` branch should get built on Travis and deployed to GitHub Pages.
