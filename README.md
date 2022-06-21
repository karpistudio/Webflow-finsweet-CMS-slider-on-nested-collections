# Webflow-finsweet-CMS-slider-on-nested-collections
This custom code will make Finsweet's CMS slider work on nested collections, e.g. on multi-image references.

## How to implement this solution in Webflow?
1. First, paste this code inside `<head>` tag of your page, [just like the docs say](https://www.finsweet.com/attributes/cms-slider "Finsweet docs") 
```javascript
<!-- [Attributes by Finsweet] CMS Slider -->
<script async src="https://cdn.jsdelivr.net/npm/@finsweet/attributes-cmsslider@1/cmsslider.js"></script>
```
2. Add **only** a class `cms-slider` to your slider. Don't apply this class to any other element.
3. Add **only** a class `cms-list` to your **nested** collection list (the list that is supposed to populate the slider). Once again, don't apply this class to any other element on the page.
4. Paste this code before `</body>` tag of your page
```javascript
<script>
const cmsList = document.getElementsByClassName('cms-list');
const cmsSlider = document.getElementsByClassName('cms-slider');

for(let i = 0; i < cmsList.length; i++){
cmsList[i].setAttribute("fs-cmsslider-element", `list-${i+2}`);
cmsSlider[i].setAttribute("fs-cmsslider-element", `slider-${i+2}`);}
</script>
```
If you want to use different class names for your slider and collection list, you can do that. If you do, don't forget to also change them in the first two lines of before `</body>` tag <script>, to match with your new class names.

You **do not need** to add custom atrributes to slider and collection list in Webflow, the script will do that for you. If you do add them, this solution will still work.
