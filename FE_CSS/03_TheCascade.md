# The Cascade

有时候两个或者更多的CSS 规则可以应用到一个element上：

- 浏览器如何选择 which rules to use
- 如何control 这个selection



The cascade is the algorithm for solving conflicts where multiple CSS rules apply to an HTML element. There are 4 distinct stages:

1. Position and Order of appearance: CSS规则出现的顺序
2. Specificity: 一个算法决定哪个CSS 选择器有最强的匹配
3. Origin：The order of when CSS appears and where it comes from, whether that is a browser style, CSS from a browser extension, or your authored CSS
4. Importance: Some CSS rules are weighted more heavily than others, especially with the `!important` rule type.



**Basic**:

The `<style>` element is declared in the `<head>` while the `<link>` element is declared in the `<body>` . This means the `<link>` gets more specificity than the `<style>` element.

Styles can come from various sources on HTML page:

- `link` tag
- Embedded `style` tag
- inline CSS as defiend in an element's `style` 

If you have a `<link>` that includes CSS at the top of your HTML page, then another `<link>` that includes CSS at the bottom of your page: the bottom `<link>` will have the most specificity. The same thing happens with embedded `<style>` elements, too. They get more specific, the further down the page they are.



CSS will not throw an error or break the program when it detects a line it cannot parse -- the value it cannot parse is invalid and therefore ignored. The browser then continues to process the rest of the CSS without breaking stuff it already understands



***An inline `style` attribute with CSS declared in it will override all other CSS, regardless of its position, unless a declaration has `!important` defined.***



**Position and Order of appearance**:

Order is applied from top to down, except for inline style and `!important` used.

Position also applied in the order of the CSS rule. 

​	Being able to specify two values for the same property can be a simple way to create fallback for browsers that do not support a particular value.

```css
.my-element {
  font-size: 1.5rem;
  font-size: clamp(1.5rem, 1rem + 3vw, 2rem);
 }
```





**Specificity**:

Specificity is the algorithm: determines which CSS selector is the most specific, using a weighting or scoring system to make those calculations. By making a rule more specific. 决定哪个CSS选择器更具体， 使用体重和分数系统

Override order:

​	id selector > class selector > element selector



This is one reason why it is generally not a good idea to attach styles to an `id`. It can make it difficult to overwrite that style with something else.



Specificity is cumulative



**Origin**: 

The cascade takes into account the origin of the CSS. 

The origin includes:

- Browser's internal stylesheet
- Styles added by browser extensions or the OS
- authored CSS

The **Order of specificity of these origins**:

1. User agent base styles: 浏览器样式表应用到HTML元素初始
2. Local User styles：这些样式可以来自于OS level， 例如，base font size， 或者 perference of reduced motion。 hey can also come from browser extensions, such as a browser extension that allows a user to write their own custom CSS for a webpage.
3. Authored CSS
4. Authored `!important`
5. **Local user styles `!important`**
6. User agent `!important`



**Importance**

The **order of importance**, from least important, to most important is as follows:

1. normal rule type
2. animation rule type
3. `!important` rule type
4. `transition` rule type

Active animation and transition rule types have higher importance than normal rules. In the case of transitions higher importance than `!important` rule types. This is because when an animation or transition becomes active, its expected behaviour is to change visual state.





***Conclusion***: The Cascade can be used for:

- Resolving conflicts when multiple styles apply to an element.
- Ensuring there's only one style value for each property at draw time.
- Scoring and weighting style rules.
- Sorting and filtering style attributes.































