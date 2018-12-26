# citizen-statistician

This is the source repository of the [Citizen Statistician](http://www.citizen-statistician.org/) blog. The blog is built with the [**blogdown**](https://github.com/rstudio/blogdown) package. If you want to build the blog locally, you can clone or download this repo, click `citizenstatistician.Rproj` to open it in RStudio, then install **blogdown** and Hugo:

```r
install.packages("blogdown")
blogdown::install_hugo()  # install Hugo
```

Now you can build and preview the website:

```r
options(servr.daemon = TRUE)
blogdown::serve_site()
```

Please note it may take a long time to render the website for the first time, but it will be faster after that.

You can add a new post via

```r
blogdown::new_post("Your Post Title")
# use the argument ext = ".Rmd" if you want an R Markdown post
```

RStudio will automatically open the post, and you can edit/preview it.

You can also add new posts with the **New Post** Addin.

This repository is set up such that when you push to the master branch the website is re-deployed automatically with Netlify. So you don't want to push to master before you're ready for your post to go live. Below are two workflows for working with this structure:

1. (Recommended) Create a new branch before adding a new post. While writing the post view it locally with `blogdown::build_site()`. When you're done, create a pull request to the master branch and merge your changes. Once you merge, the blog will rebuild and your changes will go live.

2. Add a new post in the master branch, and while writing the post only view it locally with `blogdown::build_site()` and make sure to never push your changes. When you're done, push your changes to the master branch, and Netlify will rebuild the site and publish your changes. Note that this approach is less recommended as it's natural to forget to not push your changes while writing your post. Of course, this is not the end of the world, it just means temporarily an incomplete post will be online. If this happens, you can either roll back your changes, or quickly finish your post and republish.


##  Acknowledgements

- This README is heavily based on the README of the R Views blog.
- The cover image of the blog is from Pixabay: https://pixabay.com/en/waterfall-scotland-isle-of-skye-540117/

## Tips

- Save images to imgur instead of under `/static/post/`
- For thumbnails, 236 x 236 works best

