# HUGO Tutorial

## What is HUGO ?

Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

## Steps to follow

- Getting Started
  - Install Hugo [docs/getting started/install hugo]
  - `brew install hugo` for macOs
- Create directory [folder] for project and run following command in terminal
  - `hugo new site hugo-demo -f yml` here `-f yml` is optional but we want create config files using `.yml` so we used it
- Picking a premade theme from `themes` section

  - we are using `PaperMod` theme
  - Open theme and scroll down to see installation process
  - To install make user we are in `project-directory` in terminal, if not `cd hugo-demo`
  - Next step is clone the theme repo `git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1`
  - Open Project in VSCode and open `config.yml` file

- Configuration in `config.yml` file

  - `baseURL: ""`

    `languageCode: en-us`

    `title: Demo hugo site`

    `theme: PaperMod`

- See project in browser for this run `hugo server` it will run the project and we can see the output on `localhost:1313`

- Add content to our site

  - for this run `hugo new posts/first.md` it will create `first.md` file in `content/posts/first.md`
  - By default draft flag is set to `true` it means not ready to show content on website. Please change draft flag to `false`
  - For adding image we use `cover` as written in `first.md` file
  - Add some content to our post and see the changes in browser

- Folder Structure of our project

  - `/content` It is used for all the content
  - `/layout` It is used for theme customization
  - `/static` It is used for static content like images
  - `/theme` It is used for adding pre made theme

- Now adding menus for navigation

  - open `config.yml` file and add following code
  - ```
      menu:
          main:
              - identifier: categories
                name: Categories
                url: /categories/
                weight: 10
              - identifier: tags
                name: Tags
                url: /tags/
                weight: 20
              - identifier: archives
                name: Archives
                url: /archives/
                weight: 30
    ```
  - weight is used for order of menus
  - Now update our posts with `tags` and `categories`

  - for `archives` menu we need to create `/content/archives.md` file because it is part of premade theme

- Adding hero title to our site

  - open `config.yml` and add `params:`
  - ```
      homeInfoParams:
          Title: "Hello Stranger"
          Content: <some content here>
      socialIcons:
          - name: facebook
            url: "www.facebook.com"
          - name: Twitter
            url: "www.twitter.com"
          - name: Github
            url: "www.github.com"
    ```

- Adding features to detailed post page

  - show bread crumbs `ShowBreadCrumbs: true` in `config.yml` under `params:`
  - show reading time `ShowReadingTime: true`
  - show share buttons `ShowShareButtons: true`
  - show post nav links `ShowPostNavLinks: true`

- Deployment to netlify
- First create empty git repo `git init` then `touch .gitmodules`
- add following code to `gitmodules`
- ```
    [submodule "themes/PaperMod"]
        path = themes/PaperMod
        url = "https://github.com/adityatelange/hugo-PaperMod.git"
  ```
- create repo , add code , commit and push
- netlify configuration
  - build : hugo
  - publish dir : public
  - ENV_VARIABLES : hugo_version
  - `hugo version` in terminal to get version
