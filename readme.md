# BEM, CSS Nesting and SCSS

## Learning Objectives

By the end of this lesson you should

- Understand and be able to use BEM naming convention
- Know how to use nesting with CSS Selectors
- Understand how to nest properly using by utilizing BEM
- Understand what SASS and SCSS are
- Use Variables, Partials and `&` in SCSS

## Code Along

Feel free to code along or code along

```
touch index.html style.css
```

Let's add boilerplate code to our `index.html` file

## BEM

It can be a challenge to set a consistent standard for how you are using class names across a web application. While there are many possible patterns you can follow, we will be learning one called BEM. BEM is an acronym standing for `Block` `Element` `Modifier`

### Block

A block represents a piece of HTML that must stay together for it to be useful. As an example, usually a form is made up labels, inputs and a submit button. If we separate the inputs from the labels or the submit button from the form, it would no longer work properly. We can then say that our form is a block.

We give blocks a class name that represent what it is.

```HTML
  <div class="info-card"> <!-- This is our block-->
    <div class="title">Info Card</div>
    <div class="text">
      This is an info card with some content.
    </div>
  </div>
```

### Element

An element is one of the pieces that make up the block. For example, our info card has two elements: the title and the text.

When using class names like 'title' or 'text', we run the risk of accidentally colliding with the same name in a different component. When following BEM, we will give each of them a class name made of three parts:

1. the block name - 'info-card'
2. two underscores '\_\_'
3. its own identifier = 'title'

When we put it all together it looks like this: 'info-card**title' and 'info-card**test'. By following this pattern, we have largely reduced our chances of duplicating a style somewhere else in the application to 0.

Here's what it looks like when we've changed the class names on each element:

```HTML
  <div class="info-card"> <!-- This is our block-->
    <div class="info-card__title">Info Card</div>
    <div class="info-card__text">
      This is an info card with some content.
    </div>
  </div>
```

### Modifier

Flags on blocks or elements. Use them to change appearance, behavior or state.

CSS class is formed as block’s or element’s name plus two dashes: .block--mod or .block\_\_elem--mod and .block--color-black with .block--color-red. Spaces in complicated modifiers are replaced by dash.

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="info-cards">
      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card</div>
        <div class="info-card__text">
          This is an info card with some content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card</div>
        <div class="info-card__text">
          This is another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>

      <div class="info-card">
        <!-- This is our block-->
        <div class="info-card__title">Info Card </div>
        <div class="info-card__text">
          This is yet another info card with different content.
        </div>
      </div>
    </div>

    <form class="form form--theme-xmas form--simple">
      <input class="form__input" type="text" />
      <input class="form__submit form__submit--disabled" type="submit" />
    </form>
  </body>
</html>
```

```CSS
/* Styling for the cards */
.info-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.info-card {
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  padding: 20px;
  margin: 10px;
  border-radius: 5px;
  height: 200px;
  width: 100px;
}

.info-card__title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.info-card__content {
  font-size: 16px;
  line-height: 1.5;
}

/* Styling for the form */
.form {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.form__input {
  padding: 10px;
  font-size: 16px;
}

.form__submit {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  margin-left: 10px;
}

.form__submit--disabled {
  background-color: #ccc;
  color: #999;
  cursor: not-allowed;
}
```

## Nesting CSS

As of late it is possible to nest css rules inside each other. That allows us to group together CSS rules that belong in the same block, which aligns with using BEM.

Let's change our CSS file to use nesting!
