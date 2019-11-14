# :tumbler_glass:  Whiskey makes writing happen.

Whiskey is a static site generator focusing on making writing happen. It gets
out of the way so you can focus on telling your story.

This is an example repository to help you get started using `whiskey`.

### Setup

1. Run `python3 -m pip install whiskey-flask` to install `whiskey` and it's
   requirements.
1. Whiskey is built using `flask`, so we'll interact with it through the Flask
   CLI. Do `flask run` and then navigate to
   [127.0.0.1:5000](http://127.0.0.1:5000). You should see a basic page
   that says "Hi!". Easy enough.
1. Let's turn this static site into a blog. In `site.conf`, change
   `SITE_STYLE='static'` to `SITE_STYLE='blog'` and at the bottom of the
   `site.conf` add:

       POST_DIRECTORY="posts"

1. Create the directory `content/posts`, and add a file called something like `first-post.md` with this content:

       ---
       title: Hello World
       published: True
       date: 2019-06-21 08:52:18
       description: "Nice to meet you."
       ---

       Hope we meet again.

1. Now, stop the `flask` server that's running and re-run it. Reload the page
   and you should now see a simple blog roll. Trying clicking on the blog post.
1. Let's change `SITE_STYLE` to be `SITE_STYLE='hybrid'` now. Re-run the `flask
   run` command again and if reload, you'll now see your content from
   `index.md` above your post blog roll.
1. To "freeze" your site to static files, run `flask build` and look in
   `./build`. You should see the generated content of your site.
1. If you have a server and have added the `DEPLOY` information (see below) to
   your `site.conf`, you can run `flask publish` to publish your static site to
   your server.

### Customizing Templates and Styles

So far, the example you set up is using the basic default templates and styles
in `src`. To customize your new site, all you have to do is edit these!

## Site Configuration

Here is a full example of the options available to configure a site:

```
TITLE='Title of Site'
DESCRIPTION='A description that's used various places.'
BASE_URL='https://example.com'
BASE_NAME='example.com'
NAV=[{"title": "About", "destination": "/about.html"}, {"title": "Contact", "destination": "/contact.html"}]
AUTHOR='Nick Wynja'
TIMEZONE='US/Eastern'
SITE_STYLE='blog'
POST_DIRECTORY='posts'
POST_LINK_STYLE='date'  # if you want a /yyyy/mm/post-slug style URL

FEATURED_POSTS_COUNT=2
RECENT_POSTS_COUNT=100

DEPLOY_HOST=''         # hostname or IP of server to deploy to
DEPLOY_USER=''         # ssh user
DEPLOY_PORT=''         # ssh port
DEPLOY_DIR=''          # server directory to rsync files to

BACKUP_HOST=''         # hostname or IP for backup
BACKUP_USER=''         # ssh user
BACKUP_PORT=''         # ssh port
BACKUP_DIR=''          # server directory to rsync zip to
```
