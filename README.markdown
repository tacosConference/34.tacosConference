# TaCos 2024 Website 
This is the website for the 2024 `Tagung der Computerlinguistik Studierenden` in Saarbrücken. The [Jekyll](https://jekyllrb.com/) event theme is cloned from [here](https://github.com/melvinchng/event-jekyll-theme). 

> If you want to use this website as a **template** for your conference/event, follow [these instructions](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).

## Website Documentation
Detailed information on how to use this website can be found in the [wiki](https://github.com/tacosConference/tacosConference.github.io/wiki/Basic-Website-Documentation) of this repository.

## How to clone the website
### 1. Check whether you have installed [Git](https://git-scm.com/).

In the command line, type:
```sh
git --version
``` 
If not, follow steps **the first two steps** in [this tutorial](https://docs.slam.phil.hhu.de/#/github_tut) if your are on Linux or Mac OS. For windows users, substitute the step that uses `sudo apt install git` with a download from [here](https://git-scm.com/download/win).

### 2. Install the prerequisites for the website

1. Follow the tutorial for your operating system [here](https://jekyllrb.com/docs/installation/#requirements) to install Jekyll requirements.

2. Check if you have NodeJS installed:
    ```sh
    node --version
    ```
    If not, install it with the corresponding installer for your operating system from [here](https://nodejs.org/en/download/). 

3. Download Jekyll sitemap and Jekyll SEO gems.
    ```sh
    gem install jekyll-sitemap
    gem install jekyll-seo-tag
    ```
    >Should you encounter the error below when trying to install `jekyll-sitemap` you have to install ruby dev (or look up a solution if you are on Windows):
    >```sh
    >sudo apt install ruby-dev
    >```
    Error:
    ```
    ERROR:  Error installing jekyll-sitemap:
            ERROR: Failed to build gem native extension.

        current directory: /var/lib/gems/3.0.0/gems/ffi-1.15.5/ext/ffi_c
    /usr/bin/ruby3.0 -I /usr/lib/ruby/vendor_ruby -r ./siteconf20221123-802-zy3iwm.rb extconf.rb
    mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h
    ```

### 3. Clone the website
```sh
git clone git@github.com:tacosConference/tacosConference.github.io.git
```

### Congratulations, you are done! :tada:
