---
title: "Hello World!"
date: 2023-03-28T15:28:38+02:00
draft: false
---

I wanted to start blogging for a while and as a casual follower of the generative AI hype train the obvious decision was to mess around with GPT-4. Using this little tool is like finding a new coding superpower - super convinient for well defined tasks. So let's see how this blog came to be...

### Prompt:
> *"I would like to create a simple, self-deployed blog. I am familiar with flask and node.js. I would like to store the code and posts in GitHub and I would like to deploy it with a GitActions CI on every push to the main branch. I would like to utilize Markup so my posts can be formatted. Hosting should be simple to set up and cheap. I already own a domain/url. Please generate the base project and necessary setup steps"*

If you've read a few posts about prompt engineering you already know this is horrible and could be improved in various ways to sound more like a set of specific instructions. But that is no issue for the hero of our story, GPT-4 for a simple task like this.

### Response:

> To create a simple self-deployed blog with Flask and Node.js, you can use a static site generator like Hugo. Hugo can convert your Markdown content into HTML and deploy it using GitHub Pages, which is free and simple to set up. You can use GitHub Actions to automate the deployment process.
> 
> Here's a step-by-step guide to create and deploy your blog:
> 
> #### Install Hugo.
> On macOS, you can use Homebrew to install Hugo:
> ```
> brew install hugo
> ```
> 
> On Windows, you can use Chocolatey:
> ```
> choco install hugo -confirm
> ```
> 
> For other platforms, check the official documentation.
> 
> #### Create a new Hugo site:
> ```
> hugo new site my-blog
> cd my-blog
> ```
> 
> #### Add a theme to your site (you can find more themes at Hugo Themes). Here's an example using the "Ananke" theme:
> ```
> git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
> echo 'theme = "ananke"' >> config.toml
> ```
>
> #### Create a new post:
> ```
> hugo new posts/my-first-post.md
> ```
> Edit the content/posts/my-first-post.md file to write your blog post using Markdown.
> 
> #### Run the local server to preview your site:
> ```
> hugo server -D
> ```
> Visit http://localhost:1313/ to see your blog.
> 
> #### Set up GitHub Pages.
> Create a new GitHub repository, and push your blog's code to the main branch.
> 
> In your GitHub repository, go to Settings > Pages, and select the gh-pages branch as the source branch. Save the changes.
> 
> #### Set up GitHub Actions.
> Create a .github/workflows/deploy.yml file in your blog's repository with the following content:
> 
> ```
> name: Deploy
> 
> on:
>   push:
>     branches:
>       - main
> 
> jobs:
>   deploy:
>     runs-on: ubuntu-latest
> 
>     steps:
>     - name: Checkout
>       uses: actions/checkout@v2
>       with:
>         submodules: true
> 
>     - name: Setup Hugo
>       uses: peaceiris/actions-hugo@v2
>       with:
>         hugo-version: 'latest'
> 
>     - name: Build
>       run: hugo --minify
> 
>     - name: Deploy
>       uses: peaceiris/actions-gh-pages@v3
>       with:
>         github_token: ${{ secrets.GITHUB_TOKEN }}
>         publish_dir: ./public
> ```
> This GitHub Actions workflow will build and deploy your blog to GitHub Pages every time you push to the main branch.
> 
> #### Configure your custom domain.
> In your GitHub repository, go to Settings > Pages, and enter your custom domain in the "Custom domain" section. Save the changes.
> 
> Create a CNAME file in the static directory of your blog's repository with your custom domain:
> 
> ```
> echo 'your-custom-domain.com' > static/CNAME
> ```
> Commit and push the changes.
> 
> #### Configure your domain provider.
> Go to your domain provider's settings, and add a CNAME record pointing your custom domain to *your-github-username*.github.io.
> 
> Now your blog is set up and will be automatically deployed to your custom domain every time you push to the main branch.

I am quite impressed so far with what it can do and in my personal opinion the hype is real - generative AI is a game changer for how we will work and search in the future. Humans using AI to create stuff which another AI will process and redistribute to humans. The wild west of mostly unregulated AI is upon us.