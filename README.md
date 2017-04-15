## Website Performance Optimization portfolio project

The challenge for this project is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible.

### How to RUN
This project repo is hosted on Github Pages. Open the following link and do the test:<br />
[https://sunnymary.github.io/website-optimization/](https://sunnymary.github.io/website-optimization/)

### Goals 1: Achieve a PageSpeed score of at least 90 for Mobile and Desktop - index.html.
* Link to the tool: [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/).
* Initial PageScore: Mobile - 27/100, Desktop - 29/100
#### Methods
1. Optimize images
   * resize pizzeria.jpg from 2048*1536px to middle-size(720*520px) and small-size(100*75px)
   * PageScore: Mobile - 71/100, Desktop - 85/100
2. Eliminate render-blocking JavaScript and CSS in above-the-fold content
   * remove render-blocking Javascript `http://www.google-analytics.com/analytics.js` by adding `async` keyword
   * add `media` attribute to the css link for `print.css`.
   * optimize google font by using [web font loader](https://github.com/typekit/webfontloader#google) tool.
   * change external stylesheet `style.css` to internal.
   * PageScore: Mobile - 91/100, Desktop - 92/100

### Goal 2: Render with a consistent frame-rate at 60fps when scrolling - views/pizza.html.
1. scrolling JANK
   * Use Chrome DevTool Timeline to find out the JANK symptom is forced layout trashing. The problem is caused by JavaScript - `updatePositions` function.
   * In `updatePositions` function, in the for loop, heavy math is done to reduce speed. So I move repetitive calculation from big for loop out and store pre-calculated data in an Array.(see `views/js/main.js:510`)
   * JS created 200 pizzas. But it is not necessary. I changed the pizza number from 200 to 30.(see `views/js/main.js:544`)
   * Result achieved 60fps when scrolling.

2. resizing JANK
   * Use Chrome DevTool Timeline to find out the JANK symptom is forced reflow. The problem is caused by JavaScript - `changePizzaSizes` function.
   * In `changePizzaSizes` function, there is no need to calculate the newwidth for all the pizza elements. Calcuate only one newwidth of a pizza element and apply it to all others.(see `views/js/main.js:450`)
   * Result achieved within 5ms when resizing.



