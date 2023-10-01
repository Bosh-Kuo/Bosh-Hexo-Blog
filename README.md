# Bosh's Hexo Blog
Welcome to my personal blog project built with Hexo! This README provides an overview of my blog, how to set it up locally, and some basic guidelines.

## About

This blog is a collection of my thoughts, experiences, and interests. I use [Hexo](https://hexo.io/zh-tw/index.html), a fast and powerful static site generator, to manage and publish my content. You can access my live blog at [blog.boshkuo.com](https://blog.boshkuo.com/).

## Getting Started
To set up this blog locally, follow these steps:
1. Clone the Repository
2. Install Dependencies:
```bash
npm install
```
3. Run the Development Server:
```bash
hexo server
```
4. View Your Blog Locally:
Open your web browser and navigate to http://localhost:4000 to view your blog.



## Usage
### Creating New Content
To create a new blog post or page, use the following command:
```bash
hexo new [layout] <title>
```
Replace [layout] with the layout you want to use (e.g., post, page), and \<title\> with the title of your content.

### Clean Old Static Files
To clean up old static files and caches, use the following command:
```bash
hexo clean
```

### Generating Your Site
To generate your blog, use the following command:

```bash
hexo generate
```
This will compile your content and generate the static files for your blog in the public directory.

### Deploying Your Blog
You can deploy your blog to a hosting service or web server of your choice.
For this website I used the built-in **hexo-deployer-git** tool to deploy my website to `github pages`
```bash
hexo deploy
```


## Customization
You can customize your blog by modifying the theme, updating site settings, and managing plugins. To customize the theme or configure your blog, refer to the theme's documentation and the `_config.yml` file.

