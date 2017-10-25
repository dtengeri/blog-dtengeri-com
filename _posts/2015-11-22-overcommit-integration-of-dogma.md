---
title: Overcommit integration of Dogma
layout: post
tags: elixir overcommit git
---
In my 
[previous post]({{ site.baseurl }}{% post_url 2015-11-08-keeping-your-elixir-code-style %}), I wrote about Dogma, a source code linter for Elixir projects and how can it help to keep your code consistent. I mentioned overcommit that can execute checkers on your code before every git commit.

I've added a Dogma pre-commit checker to be able to execute Dogma before every commit. The [pull request](https://github.com/brigade/overcommit/pull/298) is awaiting for  merge.

If it gets merged into overcommit, you can use Dogma in the following way:

Install overcommit to your machine:
```bash
gem install overcommit
```  

Install it into your git repository:
```bash
overcommit --install
```  

Create a file called `overcommit.yml` in your root of your git repository and configure dogma:
```yml
PreCommit:
  Dogma:
  enabled: true
  command: ['mix', 'dogma']
```  

Now, at every git commit, overcommit will run the Dogma checker and it will not allow to commit any problematic source files into your repository.