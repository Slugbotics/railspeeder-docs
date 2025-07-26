---
title: Contribution
parent: Home
nav_order: 7
layout: default
---

# Railspeeder Contribution Guide

This page documents how to contribute to this wiki.

---

## Git

Clone the project

`git clone https://github.com/Slugbotics/railspeeder-docs.git`

Checkout a branch for the page you're working on `git branch -a`

`git checkout -b new-branch` `git checkout existing-branch`

Make your changes

`nvim docs/railspeeder-....`

Commit after sustainable changes

`git commit -am "descriptive commit message`

Install dependencies

`nix develop`

Test

`bundle exec jekyll serve`

Push

`git push`

Make PR on GitHub and have it approved after testing by another member

---
