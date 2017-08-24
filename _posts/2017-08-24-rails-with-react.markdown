---
layout: post
title:  Ruby on Rails application with Reactjs
date:   2017-08-24 14:40:16
description: Time, Datetime, Weekday query to find records [ruby][ruby-on-rails]
---

Let's create a rails application along with ReactJS and other node modules.

## Install Node.js and NPM (on MAC)
*I assume MAC already have `Xcode` and `Homebrew` installed.*

In terminal:

```bash
brew install node
```

Yes, `npm` (node package manager) comes with node by default. Alternatively, we can use [`yarn`](https://yarnpkg.com/en/docs/install#mac-tab) (my preferance also `rails` prefer it :p).
> Ah, it's neecessary to use version manager for `node`. Yes, there is node version manager `nvm`. Follow [these steps](https://github.com/creationix/nvm#installation) to install it.

## Let's create a Rails application
Okay, on rails developent it's so important to pre-process JavaScript and bundle all modules, so we definately need a pre-complier which will continuously run and process asset. And for that I prefer [`webpack`](https://github.com/webpack/webpack). **Good News is**, [`rails`](https://github.com/rails) officially included `webpack` inside rails (from `5.1`) with name [`webpacker`](https://github.com/rails/webpacker)!

Now, create a rails application including `webpack` with [react](https://facebook.github.io/react/) (only for rails `5.1+`):
```bash
rails new reactapp --webpack=react
```

or just add `gem 'webpacker'` to `Gemfile` and bundle it. And then run `./bin/rails webpacker:install:react`
**Yeah sit tight, it does a lot of work :smile:**

That's it.
So, this rails application is ready with `react`. Yeah, inside `app/javascript/packs`, `react` files (`.jsx`) will remain.
Now, in `.jsx`, this type of code will render `react-dom` in Rails fornt-end:

```
document.addEventListener('DOMContentLoaded', () => {
  ReactDOM.render(
    <Hello name="React" />,
    document.getElementById("hello-world-div")),
  )
})
```
So, in `hello-world-div` react-dom will be rendered.
And finally, for continuous pre-compiling run `webpack` using this command (your prefered configuration):

```
./bin/webpack-dev-server --host example.com --inline true --hot false

```

And to add a node module use:
```
yarn add <node-module>
```

Pretty cool and easy, right? Cheers!
