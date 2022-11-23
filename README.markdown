# TaCos 2022 Website 
This is the website template for the 2022 `Tagung der Computerlinguistik Studierenden` in Düsseldorf. The template is a [Jekyll](https://jekyllrb.com/) event theme cloned from https://github.com/melvinchng/event-jekyll-theme. 

## How to clone the website
**1. Check whether you have installed [Git](https://git-scm.com/).**

In the command line, type:
```sh
git --version
``` 
You know you have git installed when you see something like `git version 2.25.1`. If you don't, follow steps 1 and 2 in [this tutorial](https://docs.slam.phil.hhu.de/#/github_tut). For windows users, substitute the step that uses `sudo apt install git` with a download from [here](https://git-scm.com/download/win).

**2. Install the prerequisites for the website**
Follow the tutorial for your operating system [here](https://jekyllrb.com/docs/installation/#requirements) and check if you have NodeJS installed:
```sh
node --version
```
If not, install it with the corresponding installer for your operating system from [here](https://nodejs.org/en/download/). 

Finally, download Jekyll sitemap and Jekyll SEO gems.
```sh
gem install jekyll-sitemap
gem install jekyll-seo-tag
```

**3. Clone the website**
In the command line, clone the website with the command below. It will be as new folder in the same folder that you run the command in. 
```sh
git clone git@github.com:tacosConference/tacosConference.github.io.git
```

You done! :tada:
