# Website guide
* [Introduction](#introduction)
* [The main page](#the-main-page)
* [Sections](#sections)
    * [Data Files](#data-files)
* [Subpages](#subpages)
* [Navigation Bar](#navigation-bar)
* [Pictures](#pictures)
* [Basic Workflows](#basic-workflows) 
    * [Change the order of the sections on the main page](#change-the-order-of-the-sections-on-the-main-page)
    * [Make a new subpage](#make-a-new-subpage)
    * [Change a picture](#change-a-picture)
    * [Make a button](#make-a-button)
    * [Change the color scheme](#change-the-color-scheme)

Instructions for hosting the website can be found in the [README](https://github.com/tacosConference/tacosConference.github.io/blob/c5f9b936c731c9bc20db9c19ba5b763b9393020f/README.markdown).

## The main page
The main page is what you land on when you load the website and includes everything that you see when you scroll down the page. It is **divided into sections** each of which is managed through a separate file in the `_includes/2023_data/` folder. 
The contents of the main page are managed in the `_layouts/2023_home.html` file.
At the top of the file you can manage the **text of the landing area**:
```html
 <div class="intro-heading">TaCoS conference<br></div>
                <div class="intro-lead-in">Dates: TBA</div>
                <div class="intro-lead-in">Saarland University</div>
```
Below that you can **arrange the order of the sections** on the main page:
```css
{% include 2023_data/newIntro.html %}
{% include 2023_data/team_members.html %}
{% include 2023_data/team_members_info.html %}
...
```
>Please note that this only changes the order of the files, NOT the content of the sections. The content of the sections is managed in the corresponding files in the `_includes/2023_data/` folder.

## Sections
Each section of the main page is managed in a separate file in `_includes/2023_data/` (altough that folder also includes other files). A file is not automatically included in the main page if it exists in that folder. A section must be referenced in the `_layouts/2023_home.html` file to be included in the main page using [`sass`](https://sass-lang.com/) syntax:
```css
{% include 2023_data/newIntro.html %}
```

At the top of each section file, there is a parameter called `id` that can be used for linking to the specific section using an [`href`](https://www.w3schools.com/tags/att_a_href.asp) html tag or oder linking mechanisms: 
```html
<section id="locations" class="bg-light-gray">
```

Some **subsections draw from data files** in the `_includes/2023_data/` folder. In this case, the html file is a template that is filled with data from the `.yml` file. This means that in order to make a change in a section, it needs to be done in the corresponding yaml file  in the `_data/twenty_23/` folder (more on that below in the section on [Data Files](#data-files)). 

For example `_includes/2023_data/team_members.html` draws from `_data/twenty_23/team_members.yml`, as can be seen in the first line below. The rest of the loop uses html and css/scss to format the data:
```css
{% for team in site.data.twenty_23.teams %}
    <div class="col-md-4 col-sm-4 speakers-item">
        <a href="#{{ team.name }}" class="speakers-link" data-toggle="modal">
            <div class="speakers-hover">
                <div class="speakers-hover-content">
                </div>
            </div>
            <img src="../css/2023_style/img/team/{{ team.thumbnail }}" class="img-responsive img-centered" alt="">
        </a>
        <div class="speakers-caption">
            <h4>{{ team.title }}</h4>
            <p class="text-muted">{{ team.subtitle }}</p>
        </div>
    </div>
{% endfor %}
```	

Some of the sections in `_includes/2023_data/` also belong together, like `team_members.html` and `team_members_info.html`, where the latter file is the information that is shown when you click on a team member on the main page. This information is also drawn from the same yaml file using sass syntax: 
```css
{% for team in site.data.twenty_23.teams %}
...
```

### Data Files
All files in `_data/twenty_23` are [`yaml`](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_yaml_tutorial.html) files. See the section above for how html and yaml files work together. 
The files are arranged in key:value pairs, similar to a [dictionary in Python](https://www.w3schools.com/python/python_dictionaries.asp). 
In order to change the information in a yaml file, change the value behind the colon, NOT the key. For example, to change the name of a team member, change the value behind `name:` in the yaml file, NOT the key itself: 
```yaml
- title: "Website Wizard"
  name: Anna Sophia Stein
  subtitle: MA Linguistics student
  img: anna.jpg
  thumbnail: anna.jpg
  alt: picture of anna
  topic: TBD
  description: TBD
```

## Subpages
Some pages have separate urls instead of being sections on the main page. These are subpages, as opposed to sections, which are managed in the `_2023_pages/` folder. 
They include, for example, the subpages of the 'More Info' section or some additional pages that we made for the 'Call for papers'.   

In contrast to the sections, the subpages are always reachable via url once the file exists in `_2023_pages/`. For example, the faq page is reachable via `https://tacos2023.github.io/faq`, even if it is not linked/referenced anywhere explicitly. The only way to make a page unreachable is to change the status of the `published` parameter in the corresponding file to `false` as shown below. 

```yaml
---
layout: 2023_default
permalink: /cfp
title: Call for Papers
published: true
---
```
The `layout` parameter refers to the design of the page, which is managed in the `_layouts/` folder (we reccommend keeping the default as it is easy to work with and plain). The `permalink` parameter is the url of the page that gets added onto the base url (`tacosconference.github.io` + `<PERMALINK>` = `tacosconference.github.io/faqs`). The `title` parameter is the title of the page, which is shown in the browser tab. The `published` parameter determines whether the page is reachable via url or not.

Anything else below the yaml header is the content of the page, which is written in html (or anything else that you want). 

## Navigation Bar
The navbar is managed by two separate files in the `_included/2023_data/` folder: `header-home.html` and `header.html`. The first one is the navbar that is shown on the main page, the second one is the navbar that is shown on all other subpages. Sometimes it is necessary to change both files, sometimes only one depending on whether you want the change to be reflected on the main page/subpages only.

You can include/exclude items from the navbar by adding them following the code block:
```html
<div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
    <ul class="nav navbar-nav navbar-right">
        <li class="hidden">
            <a href="/"></a> 
        </li>
        ...
```
Each navbar item is a list item with the syntax:
```html
<li>
    <a href="/<PERMALINK>"> <NAVBAR ITEM NAME> </a>
</li>
```
for example:
```html
<li>
    <a href="/faq"> FAQ </a>
</li>
```
The `PERMALINK` parameter is either the url of the subpage or the id of the section that you want to link. The `NAVBAR ITEM NAME` is the name that is shown on the navbar. If the permalink does not correspond to a `permalink` parameter of a subpage in `_2023_pages/`, the link will not work. 

## Pictures
All pictures are in the folder `css/2023_style/img/`. Some subfolders reference specific sections of the main page that the html file of the respective section draws pictures from. For example, the team section looks for pictures in the `css/2023_style/img/team/` folder (full code snippet above [here](#sections)):
```css
...
<img src="../css/2023_style/img/team/{{ team.thumbnail }}" class="img-responsive img-centered" alt="">
...
```
The scss parameter `{{ team.thumbnail }}` refers to the `thumbnail` key in the yaml file in `_data/twenty_23/team_members.yml`. The value of that key, the name of the picture, is therefore the name of the picture file in the `css/2023_style/img/team/` folder.	

If you want to reference pictures yourself, for example if you make a new subpage and want to include pictures, you can do it using the sass syntax or by giving the relative path to `css/2023_style/img/`.

## Basic Workflows
So you want to:
#### Change the order of the sections on the main page
- Go to `_layouts/2023_home.html` and change the order of the `include` statements (e.g. `{% include 2023_data/newIntro.html %}`)

#### Make a new subpage
- Create a new file in `_2023_pages/` including the yaml header that is included in the other files and write away

#### Change a picture
- If the picture belongs to a section, find out where the picture is being taken from in the corresponding html file in `_includes/2023_data/`. Then add the picture there and if necessary, change the value of the `thumbnail` key in the corresponding yaml file in `_data/twenty_23/` (which should correspond to the name of the file).
- Otherwise just put the picture in the `css/2023_style/img/` folder and reference it in the html file using the relative path to the picture

#### Make a button 
- `"btn-sm"`, `"btn-xl"` - small and large buttons, specified in the corresponding html element as can be seen below in the examples:
    - The 'click on me and I scroll to somewhere on the same page'- button
            - `<a href="../agenda" class="page-scroll btn btn-xl">AGENDA</a>` - scrolls to the agenda section on the main page
    - The 'click on me and I lead to another website' - button
        - `<a href="https://www.uni-saarland.de/en/home.html" class="btn-sm">Universität des Saarlandes</a>` - leads to the Saarland University website 

#### Change the color scheme
- Main color palette is set in `_data/template.yml` but a bunch of other changes may have to be made in `_includes/2023_css/agency.css`

#### Good Luck!
If you need help or have any questions, feel free to [contact Anna](mailto:anna.stein@hhu.de) from the 32. TaCoS team. 