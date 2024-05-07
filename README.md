# Christopher Moriarty - eHouse Studio Shopify Assessment
May 7, 2024

## Files Written/Adjusted
### /assets/
1. moriarty-featured-content.css
2. moriarty-header.css
3. moriarty-icon-banner.css
4. moriarty-image-with-text-card.css
5. moriarty-page-hero.css
### /sections/
1. header.liquid
2. moriarty-card-with-image.liquid
3. moriarty-featured-content.liquid
4. moriarty-hero.liquid
5. moriarty-icon-banner.liquid
### /snippets/
1. moriarty-featured-content-cared.liquid
2. moriarty-icon-hamburger.liquid
3. moriarty-search-form.liquid
## Process Overview
I started by spinning up an instance of dawn using `shopify theme init`.

From there I determined I would create 4 sections. I created the section .liquid files and their corresponding .css files in the assets folder. When building a section I try to comment where major components will exist, in most of these instances that includes comments to identify the stylesheet, image specs, main section, schema, and thinkgs like images, cards, button groups, ect.

The exception was header.liquid. Rather than creating a new moriarty-header.liquid, I decided to gut the existing header section so I could keep a few things like the 'icon-width' setting which I like intact.

After the initial setup I'll build out the HTML to be sure all the content (images, text, links) appear more or less how I want to without any styles. Then style the elements. Often during this process it becomes clear when a reusable snippet is worth making so usually build one within the section and then extract it to a separte file and `render` it.

After building a desktop-friendly section I'll add a media-query section to my css and adapt the section for mobile. Sometimes I'll opt for developing for mobile first and then going to desktop but, that is usually based on whether or not the desings for one device or the other will result in more complex styling. I'll usually do the complex one first and then strip out the complexities to achieve the simpler design.



## Code Decisions
### Separate css files
Because Dawn tends to use separate css files for most of its sections, I decided to stick with this practice. For some projects I'll opt to do section specific styles within the a `<style>` tag so its easier to find those styles later. That didn't seem necessary here.

### BEM CSS
Here I decided to stick with the Block/Element/Modifier style of CSS that Dawn seems predominant in Dawn. Sometimes I have a preferance for a more Object Oriented naming convention but I feel like Shopify Sections in general lend themselves to BEM a bit more with the exception of some elements that should probably remain universal site-wide like button styles.

### Section Padding Settings
For all sections I added settings to adjust the section padding. This is just a quick and easy tool I like to add that helps store admins achieve a bit more of the look they're after.

### Nav Link Color
How to make the 'SALE' link red? I decided to do this with an '_red_' string i the actual menu. If a link has this string, its stripped out but and the color style is set to red. Again, this allows store owners to have a quick and easy way to control this property on any link the want.

### Text Case
When text in figma was in all caps, I decided to just paste this in as is instead of using | upcase filters. In the short term this provides the store admin more flexibility though I might not select that option long term.

### Featured Content Section
This section looked like it could have been considered one for Featured Collections or, more broadly, featured content. I went with featured content. I also decided that the section would only be two 'cards' long (at most) and instead of the section blocks being the cards, it would be the card links.

If a 'block' was a card, and each card could have up to four links, it seemed like the blocks would get very cluttered. By limiting the cards to two, and then having the blocks be a link that could be assigned to card 1 or card 2, I feel like I achieved a higher level of usability for store admins.

## Questions for the Designer
### On the Hero Section
Should we add an overlay to make sure there can always be good contrast from the text to background image? Before the image switches to mobile, the dark text can be hard as the window gets smaller.

### On the Card with Image section
When on mobile, do we intend to have the text content still left aligned, both it's container and the content itself or should it be centered?

### On the Featured Content
Should this be a Featured Collection seciton or have broader usability?

How many cards should we allow each section to have? Is two per section a good maximum?

## Challenges
### Image Rendering Size
This is something that I almost always need to double check and review as far as using shopify's `| image_tag` filter so I can pass the correct srcset and other attributes to the image tag. It just isn't something that's second nature to me yet like many of liquid's other filtering methods or quirky behaviors.

### Separator Bars
Separator Bars between links and the cart icon was something that gave me a bit of pause.

For the links in the Featured Content card, I used the ~ selector which I've never used before. This allows selecting of an element if the element before it matches a selector, e.g. `.myclass ~ .yourclass` will style elements with the 'yourclass' class only if it is preceded by an element with 'myclass'.

In the header, this wasn't going to work as well due to spacing reasons and a ::before or ::after wasn't working well so I created a `<divider>` element and styled it appropriately.
