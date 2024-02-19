---
{"dg-publish":true,"permalink":"/digital-garden/digital-garden/","tags":["inbox","Portfolio"],"noteIcon":""}
---

## Instructions: How to get Digital Garden to work for Github Pages!

- Reference:  https://dg-docs.ole.dev/advanced/hosting-alternatives/

- Clone repository:  https://github.com/oleeskild/digitalgarden 
	-  (USE THIS TEMPLATE > CREATE A NEW REPOSITORY)
	- NAME THE REPOSITORY "</GITHUBNAME/>.github.io"
	
- Configure build.yml
	- https://github.com/oleeskild/obsidian-digital-garden/discussions/389

```text
#build.yml

name: GH Pages

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

# concurrency:
#   group: ${{ github.workflow }}-${{ github.ref }}

jobs:
  build:
  
    runs-on: ubuntu-22.04

    strategy:
      matrix:
        node-version: [20.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/

    steps:
      - uses: actions/checkout@v4
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'
      - run: npm install
      - run: npm run build --if-present

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GH_TOKEN2 }}  # This is from /settings/secrets/actions --> Repository secrets
          publish_dir: ./dist
```

INSTRUCTIONS FOR TOKEN --> ACTION SECRET

```text
You will need to add a GH_TOKEN secret to your repo, which should be a github API token having access to your repo. (You can reuse the one you have in your plugin settings)  
You will also need to name your repository in github, `<username>.github.io`. So in your case `efemkay.github.io`. This is because otherwise the URL will be  `<username>.github.io/<repositoryname>`. This will cause errors when the site tries to get CSS and Javascript from URLs like  `<username>.github.io/styles/style.css`, because they are actually located in `<username>.github.io/<repositoryname>/styles/style.css`.
```


https://dg-docs.ole.dev/getting-started/01-getting-started/

https://github.com/marketplace/actions/github-pages-action

https://github.com/peaceiris/actions-gh-pages

Helpful: https://www.linkedin.com/pulse/eleventy-github-pages-lea-tortay

possibly: https://github.com/peaceiris/actions-gh-pages/issues/736

and API key: https://stackoverflow.com/questions/76023778/action-failed-with-the-process-usr-bin-git-failed-with-exit-code-128

Set repository --> Settings --> Pages --> Source (Deploy from a branch): gh-pages /root

View Actions and see if they are successful!

