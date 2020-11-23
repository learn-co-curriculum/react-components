# React Components

## Overview

We'll introduce the heart of React: components. This will include explaining why
they're important and examining a few examples. If the idea and application of
components don't click immediately, _do not worry!_ The different moving parts
required to understand how to use them will fall into place as we move forward.

## Objectives

1. Understand React components
2. Create React components and show the HTML they create

## Introduction

Let's examine a high level overview of what a React component is before we
implement one. The official [React documentation on components][react-component]
says it best:

>Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

Components modularize both _functionality_ and _presentation_ in our code. In
order to understand how powerful this is, consider just how intricate web
applications can become. The difficulty in logically arranging, architecting,
and programming these web applications increases with their size. Components are
like little packages: they help us keep everything organized and predictable
while abstracting the ['boiler plate'][boiler-plate] code. Each component
contains a snippet of code that describes what it should render to the DOM.

Enough of a description &mdash; let's see some examples! While the possibilities of
what we can do with components are endless, the first thing we need to
understand about them is the ways in which they act as code templates. Let's
start simply and build up from there using a simple example.

## React Application Idea

Let's imagine we want to post a blog article describing why Bjarne Stroustrup has the [perfect lecture oration][bjarne-stroustrup]. We also want our blog article to display comments made by readers.

#### Step 1: write the components

First, let's make a component to showcase an opinion:

```javascript
class Article extends React.Component {
  render() {
    return (
      <div>
        Dear Reader: Bjarne Stroustrup has the perfect lecture oration.
      </div>
    )
  }
}
```

**Note:** You're probably used to just seeing `class Article extends Component`. Just know that `class Article extends React.Component` is an alternate syntax. Either way, it's doing the same exact thing.

Take a moment to read that code line by line:

- a new class, `Article`, is declared
- the class extends React's `component` class (which provides us with built in methods and attributes)
- the class contains a `render()` method that defines exactly what the component should render to the page

When React creates this element and adds it to the DOM, the resulting HTML will
look just as you would expect:

```HTML
<div>Dear Reader: Bjarne Stroustrup has the perfect lecture oration.</div>
```

Let's see what it would look like, were we to only render this one component, in the DOM:

![](https://curriculum-content.s3.amazonaws.com/react/component-article-example.png)

Ok, that takes care of our `Article` part of our application. Now let's make a
component to display a single user's comment:

```javascript
class Comment extends React.Component {
  render() {
    return (
      <div>
        Naturally, I agree with this article.
      </div>
    )
  }
}
```

Take the time to read that component line by line. Here is the HTML that this
would create when added to the DOM:

```HTML
<div>Naturally, I agree with this article.</div>
```

In both of our examples, React is interpreting JavaScript code and spitting out
plain old HTML that browsers will know how to represent to the user. While the
code inside the `return()` statement looks like simple HTML, it's actually JSX:
a specialized JavaScript syntax that resembles regular HTML. We will dive deeper
into JSX (which is actually quite wonderful) later.

Once we have our components in hand, it's time to actually use them.

#### Step 2: use the components

Now that we have these components written, all we need to do is make sure some
other component is making use of them in its `render` method. Every React
application has some top level component. Very often, this top level component
is simply called `App`. For our example, here's what it might look like:

```javascript
class App extends React.Component {
  render() {
    return (
      <div>
        <Article />
        <Comment />
      </div>
    )
  }
}
```

Here we can see JSX coming into play a bit more. The code inside the `return()`
still looks a lot like regular HTML, but in addition to rendering a regular old
HTML `div` element we're also rendering our two components. We've created code
that is not only well structured and modular, but also a straightforward
description of what we want the `App` component to do: render the article first,
followed by the comment. Here is what the resulting HTML will look like:

```HTML
<div>
  <div>Dear Reader: Bjarne Stroustrup has the perfect lecture oration.</div>
  <div>Naturally, I agree with this article.</div>
</div>
```

![](https://curriculum-content.s3.amazonaws.com/react/component-article-comment-example.png)

This unpacks logically. The `App` component (being our top level component)
wraps around both `Article` and `Comment`, and we already know what they look
like when they are turned into HTML.

As you may expect, we refer to the `App` component as the _parent_ component of
both the `Comment` and `Article` components. Inversely, we refer to `Comment`
and `Article` as _children_ components of `App`.

## Summary

We just introduced simplified, bare bones, React components. They are used to
house modularized front end code. In our example, as is often the case, they
contain information on how a portion of our application should be turned into
HTML.

Going forward, we will continue with this example. We will show how components
can be re-used and how they can be written as dynamic templates that contain
content that can change based on user actions.

## Resources

- [React Top-Level API](https://reactjs.org/docs/react-api.html)
- [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

[react-component]: https://reactjs.org/docs/components-and-props.html
[boiler-plate]: https://en.wikipedia.org/wiki/Boilerplate_code
[bjarne-stroustrup]: https://www.youtube.com/watch?v=JBjjnqG0BP8
