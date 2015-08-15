# hugo-agency-bengudro-theme

I totally ripped this theme off of [DigitalCraftsman][].

No I did not intend to just take his theme.  (All credits go to him.)

Nor did I intend to fork it.

Mainly I copied his theme out of frustration with a little problem that
I am having and am not sure how to resolve yet.

Please take into consideration that I am new to both Hugo and Git.
Be gentle.

### tl;dr

#### Briefly my problem is as follows:

- I followed the [Hugo Quick Start Guide][], and so I cloned the entire
  [`themes` repo][] on my local machine.
- I then modified the *Agency theme* to my liking.  All fine and dandy.
- Now I want to:
   1. `git push` my website to a [Github repo][], along with any changes
      I made to the *Agency theme*.
   2. `ssh` to my web server and `git pull` my repo/website from Github.

#### But a problem occurs when I `push` my entire Hugo website to Github:

- The `themes` subdirectory does not get pushed!
   - Here is the ouput of `git status`:

            On branch master
            Your branch is up-to-date with 'origin/master'.
            Changes not staged for commit:
              (use "git add <file>..." to update what will be committed)
              (use "git checkout -- <file>..." to discard changes in working directory)
              (commit or discard the untracked or modified content in submodules)
            
                    modified:   themes (modified content)
            
            no changes added to commit (use "git add" and/or "git commit -a")

- So let’s try to `"git add" and/or "git commit -a"` as usefully suggested:

            $ git add themes
            $ git status
            On branch master
            Your branch is up-to-date with 'origin/master'.
            Changes not staged for commit:
              (use "git add <file>..." to update what will be committed)
              (use "git checkout -- <file>..." to discard changes in working directory)
              (commit or discard the untracked or modified content in submodules)
            
                    modified:   themes (modified content)
            
            no changes added to commit (use "git add" and/or "git commit -a")
            $ git commit -m "add the themes subdirectory"
            On branch master
            Your branch is up-to-date with 'origin/master'.
            Changes not staged for commit:
                    modified:   themes (modified content)
            
            no changes added to commit
            $ git push origin master
            Everything up-to-date

- So it doesn’t work (since Git says `no changes added to commit`.)
- Being new to Git, I did a little research, and I found a [few][]
  [interesting][] [links][]
- So, if I understand correctly what is going on here: the `themes`
  subdirectory in my website is actually a submodule of my git repo,
  and I cannot push changes to a repository to which I do not have
  write permissions.  Makes perfect sense.
- But that’s not even my intention in the first place anyway.  All I
  want is to make local changes to the *Agency theme*, test said changes
  on my machine and, once satisfied, `push` my website to my Gihub repo.
- But Git understands things differently: it thinks that when I `git
  push` what I really want is to contribute my changes to
  [DigitalCraftsman][]’s *Agency theme*, and since I am not a contributor
  (no write permissions to his repo), Git simply does not push (rightly
  so) the changes I made locally to the theme.  **But that is not my
  intent!**
   - And even if it **were** my intent, I would still need write
     permissions to his repo, i.e. become a contributor to his project.
     But this wouldn’t make much sense, since any changes I will make to
     his theme are simply to suit my personal taste.

#### So it seems I have two options:

1. `deinit` the `themes` submodule, `rm -rf` the `themes` subdirectory
   and replace it with with my own `themes` subdir containing *only* 
   a copy of DigitalCraftsman’s *Agency theme*
2. Keep the `themes` submodule, but figure a way to add my modified theme
   (named `agency-bengudro` or whatever) to said submodule.

Option 1.) seems the most straighforward, but I lean towards option 2.)
for at least a couple reasons:
  - This option would in theory allow me to `push` to my personal Github
    repo all changes made locally to my personal copy of the
    `agency-bengudro` theme.
  - I may want to try a different theme in the future, so keeping an
    up-to-date submodule in my project containing all Hugo themes makes
    sense; if I want to switch themes, I could repeat this procedure:
    make a local copy (with a new name) of a theme of my choice, add
    this new theme to my git repo’s submodules, modify it and `push`
    changes to my personal Github, whitout having to become a
    contributor to any project.

I realize the above sounds like the ramblings of a newbie, but I am just
trying to figure out what would be the best approach to have my own
modified theme residing happily alongside Hugo’s “official” themes.
Any input apprecitated. 😃


[DigitalCraftsman]: https://github.com/digitalcraftsman/hugo-agency-theme/
[Hugo Quick Start Guide]: https://gohugo.io/overview/quickstart/
[`themes` repo]: https://github.com/spf13/hugoThemes/
[Github repo]: https://github.com/bengudro/bengudro/
[few]: http://www.minute.no/2015/04/setting-up-a-git-repository-with-nested-submodules/
[interesting]: https://stackoverflow.com/questions/1260748/how-do-i-remove-a-git-submodule/
[links]: https://git-scm.com/book/en/v2/Git-Tools-Submodules/

## Agency Theme

Agency Theme is a one page portfolio for companies and freelancers based on
the [original Bootstrap theme][] by [David Miller][].  This Hugo theme
features several content sections, a responsive portfolio grid with hover
effects, full page portfolio item modals, a timeline, and a contact form.

![Hugo Agency Theme screenshot](https://raw.githubusercontent.com/digitalcraftsman/hugo-agency-theme/master/images/screenshot.png)


## Contents

- [Installation](#installation)
- [Getting started](#getting-started)
    - [The config file](#the-config-file)
    - [Change the hero background](#change-the-hero-background)
    - [Present your skills](#present-your-skills)
    - [Create your portfolio](#create-your-portfolio)
    - [Show what happened](#show-what-happened)
    - [Introduce your team](#introduce-your-team)
    - [List your clients](#list-your-clients)
    - [Make the contact form working](#make-the-contact-form-working)
    - [Nearly finished](#nearly-finished)
- [Contributing](#contributing)
- [License](#license)
- [Annotations](#annotations)


## Installation

Inside the folder of your Hugo site run:

    $ mkdir themes
    $ cd themes
    $ git clone https://github.com/digitalcraftsman/hugo-agency-theme

For more information read the official [setup guide][] of Hugo.


## Getting started

After installing the Agency Theme successfully it requires a just a few more
steps to get your site running.


### The config file

Take a look inside the [`examples`][] folder of this theme.  You’ll find a
file called [`config.toml`][].  To use it, copy the [`config.toml`][] in the
root folder of your Hugo site.  Feel free to change the strings in this theme.


### Change the hero background

The hero acts as an eye-catcher for your site.  So consider to give him
a nice background.  You just need to replace the [`header-bg.jpg`][] at
[`static/img`][] with your own background image.  But it’s important
that you keep the original filename.


### Present your skills

This section should show your capabilities and skills.  You can change the
services at `[params.services.list]` in the [`config.toml`][].

All icons are part of Fontawesome’s icon font.  Look at the website of
[Fontawesome][] for more icons.  The icons are represented by their
corresponding CSS class of Fontawesome.  A skill is defined like this
example:

```toml
[[params.services.list]]
      icon = "fa-shopping-cart"
      title = "E-Commerce"
      description = "Lorem ipsum dolor sit amet, consectetur adipisicing elit.  Minima maxime quam architecto quo inventore harum ex magni, dicta impedit."
```


### Create your portfolio

Beside the [`config.toml`][], there is another subfolder called
[`projects`][] which hosts the files that will appear as your projects
in the portfolio section.  Such a project file might look like
[this one][] written in YAML:

```yaml
modalID: 1
title: Round Icons
subtitle: Lorem ipsum dolor sit amet consectetur.
date: 2014-07-05
img: roundicons.png
preview: roundicons-preview.png
client: Start Bootstrap
clientLink: "#"
category: Graphic Design
description: Use this area to describe your project.  Lorem ipsum dolor sit amet, consectetur adipisicing elit.  Est blanditiis dolorem culpa incidunt minus dignissimos deserunt repellat aperiam quasi sunt officia expedita beatae cupiditate, maiores repudiandae, nostrum, reiciendis facere nemo! <br /><br />**Want these icons in this portfolio item sample?** You can download 60 of them for free, courtesy of [RoundIcons.com](//getdpd.com/cart/hoplink/18076?referrer=bvbo4kax5k8ogc), or you can purchase the 1500 icon set [here](//getdpd.com/cart/hoplink/18076?referrer=bvbo4kax5k8ogc).
```

Copy [`projects`][] inside the `data` folder in the root directory of
your site.  Let’s make some changes.

Pay attention to the `modalID`.  It must be a unique integer and be
incremented with each new project you want to add to the portfolio.
Otherwise, the corresponding modal can’t be rendered.

Furthermore, you can use Markdown syntax for URLs like here
`[text](//url.to/source)` in the description.

To give your projects an image, save those under [`static/img/portfolio`][].
Don’t forget to set the appropriate **filename** under `img` in your project.


### Show what happened

This theme features a timeline for important events in your company or
your career too.  You can add a new event by copying the following
snippet to the `[params.about]` section in the [`config.toml`][].

```toml
[[params.about.events]]
      img = "1.jpg"
      date = "2009-2011"
      title = "Our Humble Beginnings"
      description = "Lorem ipsum dolor sit amet, consectetur adipisicing elit.  Sunt ut voluptatum eius sapiente, totam reiciendis temporibus qui quibusdam, recusandae sit vero unde, sed, incidunt et ea quo dolore laudantium consectetur!"
```

The image set under `img` needs to be stored at [`static/img/about`][].
The events will be listed from the top to the bottom.


### Introduce your team

Let the visitors or potential clients know who you are.  To add a team
member paste the code below into the [`config.toml`][].  The `img` field
refers to the shown image.  Paste those of you or your colleages into
[`static/img/team`][].

```toml
[[params.team.members]]
    img = "1.jpg"
    name = "Kay Garland"
    position = "Lead Designer"
    social = [
        ["fa-twitter", "#"],
        ["fa-facebook", "#"],
        ["fa-linkedin", "#"]
    ]
```

As you can see there’s an option to link individual social networks.
The first index of the array represents the icon (or CSS class) of
[Fontawesome][].  The last index is simply the link to the social
network profiles.


### List your clients

You can also show some of your clients.  To do so, paste the client’s
logos into [`static/img/logos`][] and add the example below to the
[`config.toml`][].

```toml
[[params.clients]]
    logo = "designmodo.jpg"
    link = "#"
```

***The logos require a dimension of 200 x 50 pixels.***


### Make the contact form working

Since this page will be static, you can use [formspree.io][] as proxy to
send the actual email.  Each month, visitors can send you up to one
thousand emails without incurring extra charges.  Begin the setup by
following the steps below:

1. Enter your email address under ‘email’ in the [`config.toml`][]
2. Upload the generated site to your server
3. Send a dummy email yourself to confirm your account
4. Click the confirm link in the email from [formspree.io][]
5. You’re done.  Happy mailing!


### Nearly finished

In order to see your site in action, run Hugo’s built-in local server.

    $ hugo server -w

Now enter `localhost:1313` in the address bar of your browser.


## Contributing

Did you find a bug or got an idea for a new feature?  Feel free to use the
[issue tracker][] to let me know.  Or make directly a [pull request][].


## License

This theme is released under the Apache License 2.0 For more information
read the [License][].


## Annotations

Thanks to [Steve Francia][] for creating Hugo and the awesome community
around the project.


[original Bootstrap theme]: https://github.com/IronSummitMedia/startbootstrap-agency/
[David Miller]:             https://github.com/davidtmiller/

[setup guide]:              https://gohugo.io/overview/installing/

[`examples`]:               https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/examples/
[`config.toml`]:            https://github.com/digitalcraftsman/hugo-agency-theme/blob/master/examples/config.toml

[`header-bg.jpg`]:          https://github.com/digitalcraftsman/hugo-agency-theme/blob/master/static/img/header-bg.jpg
[`static/img`]:             https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/static/img/

[Fontawesome]:              https://fortawesome.github.io/Font-Awesome/icons/

[`projects`]:               https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/examples/projects/
[this one]:                 https://github.com/digitalcraftsman/hugo-agency-theme/blob/master/examples/projects/2014-07-05-project-1.yaml

[`static/img/portfolio`]:   https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/static/img/portfolio/
[`static/img/about`]:       https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/static/img/about/
[`static/img/team`]:        https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/static/img/team/
[`static/img/logos`]:       https://github.com/digitalcraftsman/hugo-agency-theme/tree/master/static/img/logos/

[formspree.io]:             https://formspree.io/

[issue tracker]:            https://github.com/digitalcraftsman/hugo-agency-theme/issues/
[pull request]:             https://github.com/digitalcraftsman/hugo-agency-theme/pulls/

[License]:                  https://github.com/digitalcraftsman/hugo-agency-theme/blob/master/LICENSE/

[Steve Francia]:            https://github.com/spf13/
