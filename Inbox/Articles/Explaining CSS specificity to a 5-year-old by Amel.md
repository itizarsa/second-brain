# Explaining CSS specificity to a 5-year-old by Amelia Bellamy-Royds on CodePen

Source: Article
Status: Unprocessed
URL: https://codepen.io/AmeliaBR/post/explaining-css-specificity-to-a-5-year-old

![https://assets.codepen.io/91525/internal/avatars/users/default.png?fit=crop&format=auto&height=80&version=3&width=80](https://assets.codepen.io/91525/internal/avatars/users/default.png?fit=crop&format=auto&height=80&version=3&width=80)

---

> CSS Nerds: How would explain specificity to a 5-year-old child?
> 

I decided to take that literally, but my answer got too long even for a tweet thread. Here it is:

Explain it slowly, and with demonstrations as you go along. Before you can explain CSS specificity, first you must explain CSS, and elements, and classes, and this might be multiple lessons for a five year old…

1. A web page is made of elements that you can style. The title of the article is an element. Buttons and links are each elements. You can put an element around any words that you want to look different. 
    
    Elements can be put inside other elements, like small boxes inside big boxes.
    
    Take a very simple, unstyled web page and open the dev tools DOM inspector. Use the tool that highlights the boxes on the page when you hover over the elements in the DOM. Use the collapse/expand tool to show how elements are inside each other in the DOM, and how that matches to boxes inside each other in the visual page. Maybe edit the DOM to add a span around some text and give it a color.
    
2. Each element has a type. All buttons are the same type. Links are a different type. Titles in an article have different types depending on how important they are: h1 for the biggest title on the page, h2 for section titles, h3 for smaller ones, and so on. 
    
    Types describe what the element does. The browser gives elements simple styles based on its type.
    
    Go through your DOM tree — or use the CodePen editor! — and show the type/tag names for each element. Create some heading elements. Create a button element and a link element. Show that the default styles look very different, even though the code is similar except for the type name.
    
3. Elements can also have special properties. Some properties are decided automatically by the web browser, like whether the mouse pointer is over the element right now, or clicking it right now. Some properties are based on the attributes that also control the element's behavior, like whether an input element is for typing regular text or for picking a colour. 
    
    You can add your own special properties to the element. These are called classes. Classes don't do anything automatically, but you can use them in your style rules.
    
    Show how the focus, active, and visited styles on a link or button change as you interact with it. Show the difference between an `input[type="text"]` and an `input[type="color"]`. Wait five to ten minutes as your 5-year-old plays with the color picker and types gibberish into the text field.
    
4. So, are you ready to start adding your own colors or styles to your web page? We can tell the web browser what colors to make our elements by writing CSS rules.  
    
    Each rule has two parts: first, we tell the browser which elements to style. That's called the selector, because it selects which elements get the rule. The simplest selector is the star selector, which means select every element.
    
    The second part of the rule is inside curly brackets, and it says what styles we want to change. There are lots of styles, but we're going to start with just changing the `color`, and the `border`.
    
    In the CodePen CSS pane, make a simple `* { color: purple; }` rule. Add a `border: dotted blue;` declaration. Mention how this shows all the boxes inside boxes! Ask your 5-year-old for all their favourite colors & keep changing the text color and border color until they're bored again.
    
5. But it's a little boring when every element looks exactly the same, right? The simple styles that the browser made are different for different types of elements. We can do that, too, by changing the selector in our rule. 
    
    When you make style rules, you can say that the rule applies to all elements of a certain type, by replacing the star selector with the name of the element type. Then you can make other rules for other types of elements.
    
    Update your CSS rule with different type names, and show how different elements of the page get a style. Make a separate rule with a different tag name selector and different colors. If they're getting bored with colors, add a `font-size` declaration.
    
6. But remember how elements also have special properties? You can make your style rule only style elements with a certain property. And remember that some properties change when you do things on the web page, so you can make styles that change, too.  
    
    There are special symbols in the selector to say which type of property you're matching.
    
    You can define a rule that only applies to elements with a particular combination of type and property, or only when they have different properties at the same time.
    
    Write some class / pseudo-class selector rules, including `:hover` or `:active` rules, and show how the styles change. Get your 5-year-old to suggest which elements they want to give hover styles to, and write the selectors for them.
    
7. Selectors can get really complicated. You can decide to select an element only if it's inside a big-box element that is a particular type or that has a particular special property.  
    
    We call the big box surrounding an element its parent. If there's an even bigger box surrounding the parent, that's the grandparent.
    
    Rules can also be based on which other little boxes came before this one in the same big box (we call these sibling boxes, since they have the same parent).
    
    Make some parent or sibling rules. Again, ask your 5-year-old to suggest them & you can write the selectors. It might help to add back the `* {border: dotted;}` rule, so that the boxes inside boxes are visible again.
    
8. With all these different rules, sometimes an element gets two or more rules that disagree. Maybe one rule says all buttons should have green text, while another rule says elements with the `danger` class should have red text. 
    
    What colour should a button with the `danger` class be?
    
    Let the kid guess the answer, then write the rules and try it out.
    
9. Why is it red not green? It's because there is an order for how important each rule is. That's called **specificity**, because more specific rules, with selectors that are particular to this element, are more important than rules that are general and apply to a lot of elements.  
    
    The least specific selector is the star selector. It selects all the elements, but if those elements have a more specific rule that disagrees, the specific rule wins.
    
    However, the star selector is still stronger than the inheritance rule, which says that if you don't set a color rule for an element, then it gets the color from its parent.
    
    Add back in a `* { color: red}` rule, and show that the red only applies to the elements that you hadn't colored with another rule. Point out how elements inside a parent with a different color are now red instead of their parent's color.
    
10. Specificity also says that selectors based on special properties are more important than selectors based on type. That's why the rule for our `danger` class (special property) was more important than the rule for all buttons (type).    
    
    Selectors with more properties are more specific than selectors with just one property.
    
    And selectors with more types (like a parent type plus a child type) are more specific than selectors with just one type.
    
    But a selector with even one special property is more specific than a selector with any number of types.
    
    If two selectors have the exact same number of types and properties, than that's a tie for specificity. In that case, the last rule in the CSS wins.
    
    Get your 5-year-old to pick other elements in the web page, and come up with different possible selectors for that element, and give them conflicting color rules. See which color wins, then figure out why by counting the number of type and property components in the selector. For ties, use cut & paste in the CSS pane to show how changing the order changes the color.
    

Bonus lesson: If your five-year-old is very responsible, you can teach them that the most specific rule of all is the one you set on the element itself, with the `style` attribute instead of a selector. And that they can even override specificity, and indicate which rule is important, using `!important` on the declaration.

But be sure to give them the “With great power comes great responsibility” speech to go along with this.