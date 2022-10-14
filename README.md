# My Personal Website

## How to Develop Locally

### Install Prerequisites

1. Install Homebrew so you can install hugo and node

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Install hugo

```bash
brew install hugo
```

3. Install nodejs

```bash
brew install node
```
4. Install node packages

```bash
npm install postcss-cli
```

### Build the Website

Update the theme

```bash
git submodule update --remote
```

Build node packages in the theme

```bash
cd themes/hugo-theme-luna
npm install --production
```
Go back to the project folder

```bash
cd ../..
```

Run the website

```bash
npm install
```

Build statis pages

```bash
hugo -D
```

Run server

```bash
hugo server -D
```

## Write a new Blog Post

Create a new blog post

> Note: change "my_awesome_title" to whateber title of the post is

```
hugo new content/posts/my_awesome_title/index.md
```

You will see a new markdown file that we just created. Open it, it should already
have the header in the file.

Next let's add some tags so we can make the posts searchable and filterable. You
can always add new tags or use existing ones. Refer to other posts for existing
tags.

Once done editing the post and you are ready to publish to the website set
`draft` to `false` in the header.

```yaml
draft: false
```

Finally, `commit` and `push` to `GitHub` to update your website.
