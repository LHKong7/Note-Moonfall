# Selectors



**全局选择器**： `*`

**Type选择器**： `section` matches a HTML element directly

**Class 选择器**： A HTML element can have one or more items defined in their `class attribute` 

**ID 选择器**： 一个HTML元素应该是the only element on a page with that ID value

- tips： 任何元素拥有id状态 应该是unique value，unless you're writing very specific CSS for a single element, avoid applying styles with the `id` selector as it means you can't re-use those styles elsewhere.

**Attribute 选择器**： instruct CSS to look for attributes by wrapping the selector with square brackets `[]`

```
[data-type='primary'] {
  color: red;
}

This CSS looks for all elements that have an attribute of data-type with a value of primary, like this:

<div data-type="primary"></div>

Instead of looking for a specific value of data-type, you can also look for elements with the attribute present, regardless of its value.


[data-type] {
  color: red;
}

<div data-type="primary"></div>
<div data-type="secondary"></div>
```

Along with case operators, you have access to operators that match portions of strings inside attribute values.

```
/* A href that contains "example.com" */
[href*='example.com'] {
  color: red;
}

/* A href that starts with https */
[href^='https'] {
  color: green;
}

/* A href that ends with .com */
[href$='.com'] {
  color: blue;
}
```



**Grouping selectors**: A selector doesn't have to match only a single element. You can group multiple selectors by separating them with commas:

```css
strong,
em,
.my-class,
[lang] {
  color: red;
}

This example extends the color change to both <strong> elements and <em> elements. It's also extended to a class named .my-class, and an element that has a lang attribute.
```



**Pseudo-classes**: HTML元素在自己不同的状态, either because they are interacted with, or one of their child elements is in a certain state.single colon (`:`)

```css
/* Our link is hovered */
a:hover {
  outline: 1px dotted green;
}

/* Sets all even paragraphs to have a different background */
p:nth-child(even) {
  background: floralwhite;
}
```



**Pseudo-element**: ***Pseudo-elements differ from pseudo-classes because instead of responding to the platform state, they act as if they are inserting a new element with CSS.*** double colon (`::`).



**Complex Selectors**:  for *fine-grained control*

Although the following selectors give us more power, we can only **cascade downwards**, selecting child elements. We are not able to target upwards and select a parent element.

- Combinators: what sits between two selectors

  - `>` : use these combinators help user select items based on their position in the document

  - Descendant combinator: allow users to target the child element by using `space( )`

    - Because the descendant combinator is **recursive**, the padding added to each child element applies, resulting in a staggered effect.

  - Next sibling combinator: look for an element that immediately follows another element by using a `+` character in your selector.

    - You could add margin to all child elements of `.top`, using the following selector:

      

      ```css
      .top * + * {
        margin-top: 1.5em;
      }
      
      /* Presentation styles */
      .top p {
        border: 1px solid var(--color-primary);
        background: var(--color-light);
        padding: 1em;
      }
      
      /* Presentational styles */
      .top > * + * {
        position: relative;
      }
      
      .top > * + *::before {
        content: "";
        width: 100%;
        height: 1.5em;
        background: #ff807b;
        position: absolute;
        bottom: 100%;
        left: 0;
        outline: 1px solid #9d0600;
      }
      ```

    

  - Subsequent- sibling combinator: A subsequent combinator is very similar to a next sibling selector. Instead of a `+` character however, use a `~` character.  *How this differs is that an element just has to follow another element with the same parent, rather than being the next element with the same parent.*

    - We can use a **subsequent selector** along with a ``:checked`` pseudo class to create a pure CSS switch element.

      ```css
      :checked ~ .toggle__decor {
        background: rebeccapurple;
      }
      
      :checked ~ .toggle__decor .toggle__thumb {
        transform: translateX(var(--metric-toggle-thumb-size)) rotate(270deg);
      }
      ```

      

  - Child combinator allows users more control over the recursion that comes with combinator selectors. By using `> `character, you limit combinator selector to apply only to direct children.

    - To alleviate this problem, change the **next sibling selector** to incorporate a child combinator: `> * + *`. The rule will now **only** apply to direct children of `.top`.

**Compound selectors**:

You can combine selectors to increase specificity and readability. For example, to target `<a>` elements, that also have a class of `.my-class`, write the following:

```css
a.my-class {
  color: red;
}
```

















