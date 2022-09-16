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
