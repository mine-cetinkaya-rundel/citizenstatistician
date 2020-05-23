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

## Adding a new post

This repository is set up such that when you push to the master branch the website is re-deployed automatically with Netlify. So you don't want to push to master before you're ready for your post to go live.

The main recommendation is to create a new branch, create a new post in the new branch, and then submit a pull request to the master branch. Then, view the Netlify deploy preview on GitHub, and merge if you're happy with what you see. 

Below are step-by-step instructions using the [pull request helpers](https://usethis.r-lib.org/articles/articles/pr-functions.html) from the **usethis** package.

1. Launch the RStudio project on your machine by double clicking on `citizenstatistician.Rproj`.

2. Make sure you're on the master branch, and pull to get the latest changes.

3. Load the blogdown and usethis packages.

```r
library(blogdown)
library(usethis)
```

4. Serve the site locally to make sure everything builds fine locally before you start adding your own changes.

```r
blogdown::serve_site()
```

5. Initiate a pull request.

```r
usethis::pr_init("shorthand-for-blog-title")
```

6. Add a new post using the **New Post** Addin (recommended) or via

```r
blogdown::new_post("Your Post Title")
# use the argument ext = ".Rmd" if you want an R Markdown post
```

RStudio will automatically open the post, and you can edit/preview it.

7. Commit your changes.

8. Push your changes with `usethis::pr_push()` and complete the pull request on GitHub. 

If when you run `usethis::pr_push()` you get an error saying (an error that probably says `"Push errored, Check that the PR branch is editable, then check your git2r config"`, go to the Terminal window instead and type

```
git push
```

which will suggest that you alter that command a bit and run it again. It should make a recommendation for how you should alter it, and it should look like

```
git push --set-upstream origin [NAME OF YOUR BRANCH]
```

where `[NAME OF YOUR BRANCH]` is the name you gave to your branch when you ran `pr_init()` at the very beginning of this saga.

9. Once checks are completed, view the Netlify deploy preview to make sure all looks as intended. If yes, merge away! If not, come back to RStudio and make changes, commit, push, and view your changes on the Netlify deploy preview agian.


##  Acknowledgements

- This README is heavily based on the README of the R Views blog.
- The cover image of the blog is from Pixabay: https://pixabay.com/en/waterfall-scotland-isle-of-skye-540117/

## Tips

- Save images to imgur instead of under `/static/post/`
- For thumbnails, 236 x 236 works best

