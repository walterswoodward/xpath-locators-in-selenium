# xpath-locators-in-selenium
https://www.udemy.com/user/dimashyshkin/

Code examples for XPath locators for Selenium course on Udemy
Use code NINENINENINEGIT to get any my course for just $9.99 here https://www.udemy.com/user/dimashyshkin/

# Walter's Personal Notes:

## Lecture 3: Selenium Locators
### Performance:
  * CSS is considered the fastest, while xPath is the slowest. The actual discrepency is not big, we're talking 15ms MAYBE. XPath, short for XML Path Language:
    * CSS Selectors
    * XPath
      * Pros: 
        * Allows precise locators
        * Can be used on any element
      * Cons:
        * Most Complicated Locator
        * Slower
## Lecture 4: Locating Web Elements
* Using google chrome's Ranorex Selocity extension, you can then right click any element on the page, and click "Selector actions/Copy xPath". 
  * *TIP: If you are given a absolute/root path, you will likely want to shorten it, as file structure is bound to change, which would break your tests if you are using the full xPath e.g. shorten /html/body/div[2]/div/div/form/div/div/label (copied through Firefox) first by looking at xPath outputs from other sources (Chrome Inspector, Ranorex Salocity)
    * Chrome Inspector: //*[@id="forgot_password"]/div/div/label
    * Ranorex: /html//form[@id='forgot_password']//label[.='E-mail']
  * Dimi recommends shortened version of Ranorex: //label[.='E-mail']
  * You can view ALL nodes/elements that match the above xPath by running the following directly in the Chrome Inspector Console:
    * $x{"//label[.='E-mail']"} -- remember that you can also do this in Chrome via the `Element` panel search bar
## Lecture 6: Types of XPath
  * Dimi goes through manually finding the absolute path via the Elements panel in Chrome Inspector. Wonder if there is an easier way to do this?
  * If the structure of the page is changed, your absolute path will no longer be valid e.g. using the aboslute path from above, if use the following xPath in your tests: $x{"/html/body/div[2]/div/div/form/div/div/label"}, and then the structure is changed, this will result in an empty array HOWEVER, if you use the shortened xPath recommended by Dimi: $x{"//label[.='E-mail']"}, then structural changes will not impact your tests.
## Lecture 7: XPath Terminology
  * Types of Nodes:
    * Element Nodes: e.g. html, head, body, div, label, input, button etc.
    * Attribute Nodes: e.g. class, id, for, name, method, type
    * Text Nodes: Any element containing text e.g. <div> Hello </div>
    * Atomic Values: Nodes with no children
## Lecture 8: xPath Expressions and Syntax
  * single slash - `/` - Look for elements starting from the `root` node
  * double slash - `//` - Look for elements anywhere in the document
  * Exercise:
    * $x{"/div"} - searches for `div` elements inside of `root`
    * $x{"//div"} - searches for `div` elements anywhere in html document
  * Predicates Exercises:
    * attribute specific: $x{"//div[@id]"} - returns all `div` elements which have attribute `id`
    * value specific: $x{"//div[@id="content"]"} - returns all `div` elements with `id="content"`
    * 