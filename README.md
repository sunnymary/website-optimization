## Website Performance Optimization portfolio project

The challenge for this project is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible.

### How to RUN
This project repo is hosted on Github Pages. Open the following link and do the test:<br />
[https://sunnymary.github.io/website-optimization/](https://sunnymary.github.io/website-optimization/)

### Goals 1: Achieve a PageSpeed score of at least 90 for Mobile and Desktop.
* Link to the tool: [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/).
* Initial PageScore: Mobile - 27/100, Desktop - 29/100
#### Methods
1. Optimize images
   * resize pizzeria.jpg from 2048*1536px to middle-size(720*520px) and small-size(100*75px)
   * PageScore: Mobile - 71/100, Desktop - 85/100
2. Eliminate render-blocking JavaScript and CSS in above-the-fold content
   * remove render-blocking Javascript `http://www.google-analytics.com/analytics.js` by adding `async` keyword
   * add `media` attribute to the css link for `print.css`.
3. Leverage browser caching

### Goal 2: Render with a consistent frame-rate at 60fps when scrolling.


### Goal 3:


