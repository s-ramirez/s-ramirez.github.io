---
layout: post
title:  "Switching Sublime Text to Atom"
description: After more than a year using Sublime Text I decided it was time to give Github's new tool a try.
comments: True
permalink: /switching-from-sublime-to-atom
---

As a Sublime Text user for more than a year, I took the personal challenge (it's harder than it sounds) of switching the text editor I used daily for web development purposes. It's been a week since I've made the change and this is my experience so far.

## Why?

No special reason, Sublime Text provides me with all the functionality I've needed for my projects. Still, for the sake of trying out new applications and (as a web developer) exploring the capabilities of this "hackable" text editor developed by one of my favorite companies, I decided to try and make the change.

## Initial Configuration

One of the first changes I wanted to make was reduce the font size of the text editor. Not sure why it didn't felt good initially. Luckily it was as easy as going into Settings (&#8984; + ',') and changing *Font Size* to 12 and *Line Height* to 1.5 also I'm obsessed with code indentation so I checked *Show Indent Guide* and as a tab indenter, increased the *Tab Length* to 4.

## Plugins

Just as Sublime, Atom provides a lot of extensibility via Plugins. These are the ones I installed in order to feel more comfortable:

* [file-icons](https://github.com/DanBrooker/file-icons): display file-type icons in sidebar tree-view.
* [open-last-project](https://github.com/danielmahon/atom-open-last-project): I was used to just opening my editor and continuing where I left off in my projects.
* [open-terminal-here](https://atom.io/packages/open-terminal-here): Use this *a lot* when working with projects that use task automation tools like Grunt or Gulp.
* [sublime-tabs](https://github.com/ddavison/sublime-tabs): I got very used to switching between files searching for a specific value or just for a reference and didn't really want to open the file, just preview it. In Sublime Text I could preview an item by clicking it and it would open with double click. As the name suggests, this plugin allows Atom to copy Sublime's behavior.

## Themes

This section, *for me*, is probably far more relevant than it should. I personally like having dark themes on my development tools plus a syntax highlighter for the files I mostly work on (CSS, LESS, SASS, JS, HTML). Atom gives you the option to set a theme for the sidebar tree view (which is nice) and a different one for the text editor per se. I finally settled for *Atom Dark* as a UI Theme and *No Caffeine* as the Syntax Theme.

## Thoughts

With just one week I'm already getting used to the change, there is still a lot to learn from Atom (I love having the ability to just open the Developer Console and fiddling around as in websites) and hope to be able to give back to the community via either a pull request if I find somewhere I might help or a plugin.
