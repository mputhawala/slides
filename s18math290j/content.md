* Press 'o' for overview mode

* Use arrow keys to navigate presentation

* Organization is top to bottom, left to right




-vertical-

Open a web browser if you want to follow along

Chrome, Firefox, Internet Explorer, etc




-vertical-

* **GitHub**: hosting, version control

* **Reveal.js**: presentations

* **Jekyll**: websites

[jacob.moorman.me/slides/s18math290j/](https://jacob.moorman.me/slides/s18math290j/)




-horizontal-

## Github

Create an account at [github.com/join](https://github.com/join)

<img src="./images/github_create_account.png" width="45%">




-vertical-

Verify your email address

<img src="./images/verify_email.png" width="100%">




-vertical-

Options for creating a new project:

* Create a new empty repository

* Import code from an existing repository

* **Fork an existing repository**




-vertical-

Create a new empty repository

<img src="./images/new_repository_button.png" width="70%">




-vertical-

* Give your repository a name
* Tick "Initialize this repository with a README"
* Click "Create repository"

<img src="./images/new_repository_dialogue.png" width="50%">




-vertical-

Import code from an existing repository

<img src="./images/import_repository_button.png" width="80%">




-vertical-

* Paste a link to the existing repository
* Give your new repository a name
* Click "Begin import"

<img src="./images/import_repository_dialogue.png" width="45%">




-vertical-

Fork an existing repository

<img src="./images/fork_repository_button.png" width="80%">




-vertical-

Enable GitHub Pages web publishing 

<img src="./images/repository_settings.png" width="100%">




-vertical-

* Select "master branch"
* Click "Save"

<img src="./images/enable_github_pages.png" width="50%">




-vertical-

* Check that a confirmation message appears

<img src="./images/github_pages_published.png" width="100%">




-horizontal-

## Reveal.js

Examples/Demonstrations

* [Reveal.js overview slides](https://revealjs.com/)

* [My 285J presentation](https://jacob.moorman.me/slides/s18math285j/)

* [This very presentation](https://jacob.moorman.me/slides/s18math290j/)




-vertical-

## Reveal.js

* beautiful html presentations

* slides exist in a 2d grid

* slides are ordered top-to-bottom, left-to-right




-vertical-

Fork [github.com/jdmoorman/slides](https://github.com/jdmoorman/slides)

<img src="./images/fork_revealjs.png" width="100%">




-vertical-

<img src="./images/forking_revealjs.png" width="80%">




-vertical-

When finished, open the settings tab

<img src="./images/repository_settings.png" width="80%">




-vertical-

Scroll down until you see the "GitHub Pages" section

Change the GitHub Pages branch to "master branch"

<img src="./images/github_pages_branch_becomes_master.png" width="65%">




-vertical-

## Checkpoint

<img src="./images/slides_published_success.png" width="90%">

You should be able to load

[[username].github.io/slides/template/](https://mrmoorman.github.io/slides/template)




-vertical-

## Next steps

* Editing files online
* Adding content




-vertical-

Enable editing at [prose.io](https://prose.io)

<img src="./images/prose_landing.png" width="40%">




-vertical-

Authorize prose to access your repositories

<img src="./images/enable_prose.png" width="45%">




-vertical-

Open the "slides" repository

<img src="./images/prose_projects_page_1.png" width="100%">




-vertical-

Open the "template" folder

<img src="./images/template_folder.png" width="100%">




-vertical-

To edit your presentation

edit the code in "content.md"

<img src="./images/editable_content.png" width="100%">




-vertical-

To add inline equations such as \\( c = \sqrt{a^2+b^2} \\), surround with `\\(  \\)`

```
\\( c = \sqrt{a^2+b^2} \\)
```

To add block equations such as \\[ c = \sqrt{a^2+b^2}, \\] surround with `\\[  \\]`

```
\\[ c = \sqrt{a^2+b^2} \\]
```




-vertical-

Try adding this equation to your presentation:
```
\\[ c = \sqrt{a^2+b^2} \\]
```
and verify that it renders correctly.

[[username].github.io/slides/template/](https://mrmoorman.github.io/slides/template)




-vertical-

To add a new slide in the current column, use

```markdown
-vertical-
```

To add a new slide and start a new column, use

```markdown
-horizontal-
```




-vertical-

To view a summary of Markdown formatting, google "Markdown Cheatsheet" and click the first link




-horizontal-

## Jekyll

A website generator

Commonly used for blogs




-vertical-

For example: [jacob.moorman.me](https://jacob.moorman.me)

<img src="./images/my_website_example.png" width="70%">




-vertical-

Was generated from

<img src="./images/about_page_source_code.png" width="100%">

barely any more code than just the text on the screen




-vertical-

For this tutorial, I've chosen the template "Hyde". However, most templates function similarly.

<img src="./images/hyde_demo_img.png" width="70%">




-vertical-

Fork [github.com/jdmoorman/hyde](https://github.com/jdmoorman/hyde)

<img src="./images/fork_hyde.png" width="100%">




-vertical-

<img src="./images/forking_hyde.png" width="100%">




-vertical-

Open the settings tab, change the name

to [username].github.io, and click rename

<img src="./images/change_repo_name.png" width="60%">




-vertical-

Scroll down until you see the "GitHub Pages" section

Change the GitHub Pages branch to "master branch"

<img src="./images/github_pages_branch_becomes_master.png" width="65%">




-vertical-

Open a tab of prose.io and
open the username.github.io repository

<img src="./images/prose_with_hyde.png" width="65%">




-vertical-

open "\_config.yml"

<img src="./images/open_config.png" width="65%">




-vertical-

On line 14, change

```markdown
baseurl:         /hyde
```

to

```markdown
baseurl:         /
```

and save the file




-vertical-

## Checkpoint

You should be able to load [[username].github.io](https://mrmoorman.github.io/)

<img src="./images/first_look_at_hyde.png" width="65%">




-vertical-

Back in "\_config.yml", change

```markdown
title:            Hyde
description:      'A brazen two-column ...'
url:              https://jacob.moorman.me/hyde/
```

to

```markdown
title:            Your Name
description:      'A brief description of yourself'
url:              https://username.github.io/
```

and save the file




-vertical-

also change

```markdown
author:
  name:           'Jacob Moorman'
  url:            https://jacob.moorman.me/
```

to

```markdown
author:
  name:           'Your Name'
  url:            https://username.github.io
```

and save the file







