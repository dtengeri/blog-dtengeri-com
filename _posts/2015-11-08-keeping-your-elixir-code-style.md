---
title: Keeping your Elixir code style consistent
layout: post
tags: elixir overcommit
---

Working with different people in a team can introduce inconsistencies into your source code. Everybody has a different coding style and your codebase can quickly become a mess. To solve this, the team can introduce a coding style guide, which describes different rules that should be applied by everybody in your team. If you have a lot of rules it is hard to remember each of it.


To help the developers, you can introduce a code style linter that inspects your source code and highlights problems in your code. There are such tools for Javascript ([JSHint](http://jshint.com/), [ESLint](http://eslint.org/)) and for Ruby too ([Rubocop](https://github.com/bbatsov/rubocop)). The rules are defined by the developer community and also applies best practices.


We usually add these linters as pre commit hooks to git, so problematic code can not be pushed to the repository. I recommend [overcommit](https://github.com/brigade/overcommit) for this, it has built in support for Rubocop and ESLint.


I found such linter for Elixir, its name is Dogma. You can find its repository on [Github](https://github.com/lpil/dogma).
At the time of writing this post, it has [27 rules](https://github.com/lpil/dogma/blob/master/docs/rules.md).


Its usage is very simple, just add it as a dependency to your `mix.exs`:

```elixir
# mix.exs
def deps do
  [
    {:dogma, "~> 0.0", only: :dev},
  ]
end
```  

Update your dependencies:  

```bash
mix deps.get
```  

And run it:

```bash
mix dogma
```  

If there are problems in your source code, you will get a a report like this:

```
== web/controllers/hello_controller.ex ==
7: FinalNewline: End of file newline missing
2: HardTabs: Hard tab indention. Use spaces instead.
4: HardTabs: Hard tab indention. Use spaces instead.
5: HardTabs: Hard tab indention. Use spaces instead.
6: HardTabs: Hard tab indention. Use spaces instead.
1: ModuleDoc: Module Sample.HelloController is missing a @moduledoc.
```