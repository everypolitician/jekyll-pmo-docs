# jekyll-pmo-docs

## Creating a new site

First you'll need to create a Jekyll repository for the new site.

    $ jekyll new my_pmo_site
    $ cd my_pmo_site

### Extract info pages and blog posts

If you're creating a site from an existing Pombola then you'll want to get the info pages and blog posts from the database.

You can get a copy of the database by visiting `/media_root/dumps/pg-dump.sql.gz` on a Pombola install. For example at the time of writing the Mzalendo database dump can be obtained from http://info.mzalendo.com/media_root/dumps/pg-dump.sql.gz.

The you'll need to import the data into a local PostgreSQL database. The following steps show this process on a Mac with PostgreSQL installed with Homebrew.

```
$ createdb mzalendo
$ psql mzalendo
psql (9.5.0)
Type "help" for help.

mzalendo=# CREATE EXTENSION postgis;
CREATE EXTENSION
mzalendo=# \q
$ psql mzalendo < /usr/local/Cellar/postgis/2.2.1/share/postgis/legacy_minimal.sql
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
CREATE FUNCTION
$ psql mzalendo < pg-dump.sql
SET
SET
SET
SET
SET
SET
SET
SET
CREATE TABLE
CREATE SEQUENCE
ALTER SEQUENCE
[ snip ]
```

Once you've got a working database you can then extract the info pages.

Install the [`pombola_extract_info_pages`](https://github.com/mysociety/pombola_extract_info_pages) gem, then run it from the directory containing your new Jekyll site.

      $ DATABASE_URL=postgres://localhost/mzalendo pombola_extract_info_pages

This will generate a file for each info page in `info` and a file for each blog post in `_posts`.
