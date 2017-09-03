
## H1 Frontend-Nanodegree-Mobile-Portfolio
This project is an example portfolio site that is customizable to deliver the author's desired content
The original code had a number of intentionally performance detrimental code uses that have largely been eliminated via the performance optimizations detailed later in this document

## H1 How to use
To run this application open index.html in your preferred browser.
Steps required to modify the content of this application are outside the scope of this document

## H1 Performance optimizations
## H2 In index.html & general
1. Removed link to google fonts
2. Added webfont loader to load google fonts
3. Ran critical path CSS generator https://jonassebastianohlsson.com/criticalpathcssgenerator/
4. Minified and inlined critical path CSS
5. Moved CSS load to end of html body
6. Compressed images, resized pizzeria.jpg created pizzeria-small.jpg
7. Replaced perfmatters.js, profilepic.jpg, and /css/style.css with Pagespeed Insights optimized versions

## H2 In main.js
1. In function changePizzaSizes - moved dx and newwidth calculations out of for loop to prevent
  layout calculations with every loop (line 451)
2. Updated sliding pizza function to calculate necessary number of pizzas on page load (line 529-531)
3. In function updatePositions, added var scrollTopCache to remove phase calculations
  from CRP ala the source work @https://www.igvita.com/slides/2012/devtools-tips-and-tricks/jank-demo.html
4. In function changePizzaSizes - replaced multiple DOM queries with a single query to store pizza element info in var randomPizzas, change selector query to getElementsByClassName from querySelectorAll
5. Moved creation of var pizzasDiv outside of for loop so DOM query is not looped
