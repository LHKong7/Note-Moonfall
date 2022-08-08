# Specificity



**Specificity Scoring**: Each Selector rule gets a scoring. Specificity can be considered as a total score and each selector type earn points towards that score. 



分数结果过高可能会导致计算缓慢：

With specificity in a real project, the balancing act is making sure the CSS rules you expect to apply, actually *do apply,* while generally keeping scores low to prevent complexity. The score should only be as high as we need it to be, rather than aiming for the highest score possible. In the future, some genuinely more important CSS might need to be applied. If you go for the highest score, you'll make that job hard.



**Scoring each selector type**



- **Universal selector**: has no specificity and get 0 points, This means that any rule with 1 or more points will override it.

- **Element or pseudo-element selector**: An Element type (div, p) or pseudo-element (::selection) selector gets 1 point of specificity

- Class, pseudo-class or attribute selector: A [class](https://developer.mozilla.org/docs/Web/CSS/Class_selectors), [pseudo-class](https://developer.mozilla.org/docs/Web/CSS/Pseudo-classes) or [attribute](https://developer.mozilla.org/docs/Web/CSS/Attribute_selectors) selector gets **10 points of specificity**.

  ​	The [`:not()`](https://developer.mozilla.org/docs/Web/CSS/:not) pseudo-class itself adds nothing to the specificity calculation. However, the selectors passed in as arguments do get added to the specificity calculation.

  ```css
  div:not(.my-class) {
    color: red;
  }
  ```

  This sample would have **11 points** of specificity because it has one type selector (`div`) and one class *inside* the `:not()`.

- ID selector

  An ID selector gets **100 points of specificity**, as long as you use an ID selector (#myID) and not an attribute selector

- Inline Style Attribute: CSS applied directly to the `style` attribute of the HTML element, gets a **specificity score of 1,000 points**. This means that in order to override it in CSS, you have to write an extremely specific selector.

- `!important` rule: an `!important` at the end of a CSS value gets a specificity score of **10,000 points**. This is the highest specificity that one individual item can get.



Visualizing Specificity:

1 - 3 - 0

The left group is `id` selectors. 

The second group is class, attribute, and pseudo-class selectors. 

The final group is element and pseudo-element selectors.



**Programmatically Boost Specificity**: using two class



Matching Specificity Score sees the **newest** instance win.

