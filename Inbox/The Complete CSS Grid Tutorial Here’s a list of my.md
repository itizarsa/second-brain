# The Complete CSS Grid Tutorial. Here’s a list of my best web… | by JavaScript Teacher | Medium

Source: Article
Status: Unprocessed
URL: https://jstutorial.medium.com/css-grid-tutorial-filling-in-the-gaps-c596c9534611

![https://miro.medium.com/max/1200/1*Gaf0_LQb7gJqxeCv2vBExA.png](https://miro.medium.com/max/1200/1*Gaf0_LQb7gJqxeCv2vBExA.png)

---

Here’s a list of my best web development tutorials.

**[Complete CSS flex tutorial](https://semicolon.dev/tutorial/css/complete-css-grid-tutorial)** on Semicolon.

**[Complete CSS flex tutorial](https://jst.hashnode.dev/complete-css-flex-tutorial)** on Hashnode.

**[Ultimate CSS grid tutorial](https://jst.hashnode.dev/css-grid-tutorial)** on Hashnode.

**[Higher-order functions .map, .filter & .reduce](https://jst.hashnode.dev/javascript-higher-order-functions-map-filter-and-reduce)** on Hashnode.

You can **[follow me on Twitter](https://www.twitter.com/js_tut)** to get tutorials, JavaScript tips, etc.

To get a good idea of how flex works try **[flex layout editor](http://www.csstutorial.org/flex-both.html)** on this page.

During my job interview at a Texas software company back in 2017 the team lead has introduced me to the idea that computer scientists (*and probably scientists in general*) make progress by *filling in the gaps*.

***That idea stuck with me.***

I don’t know but maybe like me, you found yourself trying to fill in the gaps learning CSS grid. Just as it ought to happen, every time some new tech emerges on the unsuspecting JavaScript crowd.

This tutorial was created by applying this ideology in preparation for working on the **Visual Dictionary** — My *postmortem* to CSS when I decided to take all of the existing *413* CSS properties and visualize them by making diagrams.

While primarily I consider myself a JavaScript programmer I’d like to think that I also lean a bit toward the graphic design mindset as well. Perhaps I took the idea of gaps out of context when I applied it to ***CSS grid*** in this tutorial.

***But bear with me.***

As web and graphic designers the key to ***CSS grid*** lies in grasping not the *visible* parts of layout design but ones that are not.

***Let me explain.***

***Book designers*** care about margins – essentially an *invisible* element of book design. It may not seem like much but ***remove margins*** — *the element that the reader is least aware of*— ***and the whole reading experience turns awkward.***

> Readers notice lack of margins only when they are absent.Therefore — as a designer (of anything) it is imperative to pay equal attention to the invisible elements of design.
> 

We can always just plug in the content into the layout. Could it be then… that when we design with CSS grid, all we’re doing here to create beautiful layouts is working with an ***advanced* version of book margins?** Could be.

***The gaps.***

Of course CSS grid goes way beyond designing margins in books but the principle of the so-called *invisible design* remains the same. Things we cannot see are important. In CSS grid this concept is thought of as ***gaps***.

A CSS grid after all is just like taking book margins to the next level. Sort of.

## **Creating Your First CSS Grid**

First… we will need a ***container*** and some ***items**.*

A CSS grid **flow** can go in either direction. But by default it’s set to **row**.

This means that ***if*** all other defaults are *untouched* your items will automatically form a single **row** where each item inherits its width from the grid’s container element:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1THSFGEktLGSwvm70pkyFPQ.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1THSFGEktLGSwvm70pkyFPQ.png)

To create a **CSS grid** from a blocking element simply set its **display** property to **grid**. Note that by **default grid-auto-flow** is set to row. This is why your items will “flow” over to the next row. However, if you need to change direction of the auto flow to columns you can do so by setting **grid-auto-flow** property to a value of **column**.

**CSS Grid Container**

Your CSS grid container is a <**div**> element with: ***display: grid;** and **grid-template-columns** and/or **grid-template-rows** properties that define… you guessed it… rows and columns.*

**Grid Items**

Your CSS grid *items* are <**div**> elements inside your container. Each item behaves similar to a <**td**> tag in a <**table**> but with a lot more flexibility.

All that is just basic HTML.

## CSS Grid Template

When making CSS grid layouts we’re essentially defining a template. The grid will take up the empty space on the page, regardless of whether the number of items provided (3 divs in this case) fits into the template area in its entirety:

In this case CSS grid will assume that any new items added to the grid will fall into dashed squares unless other modifications are provided… at which we will look throughout this tutorial.

Let’s start with this really small template to demonstrate some core concepts.

## Introducing… Minimalist 2-Column Design

Let’s dig down to the core of CSS grid by using minimum parameters:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/15GP7WpgE27Q1wOVxrHsHdA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/15GP7WpgE27Q1wOVxrHsHdA.png)

To start getting to know CSS grid, let’s take a look at this first simple example. Here we have **grid-template-columns** and **grid-template-rows** CSS properties defining basic **CSS grid layout**. These properties can take multiple values (which you should *separate by space*) that in turn become **columns** and **rows**. Here we used these properties to define a minimalist CSS grid composed of **two columns** (**100px** **160px**) and **one row** (**25px.**) In addition, the ***gaps*** on the *outside border* of the grid container do not add extra padding even when *gap size* is defined. Therefore they should be thought of as defined right on the edge. The gaps in between columns and rows — on the other hand — are the only ones that are affected by ***gap size***.

One thing you will notice about CSS grid right away is the definition of ***gaps***. This is different from what we’ve seen in any other CSS property before. Gaps are defined numerically starting from the upper left corner of the element.

There are ***columns+1*** gaps between columns & ***rows+1*** gaps between rows.

CSS grid does not have a default *padding*, *border, or margin* and all of its items are assumed to be ***content-box*** by default. Meaning, content is padded on the inside of the item, not outside like in all other common blocking elements.

That’s one of the best things about CSS grid in general. Finally we have a new layout tool that treats its box model as ***content-box*** by *default.*

Gap size is set individually per row or column by ***grid-row-gap*** and ***grid-column-gap*** properties or *together* by ***grid-gap*** for short.

## **Automatic (Implicit) Rows and Columns**

*CSS grid* automatically adjusts position of each item on the grid depending on size and span of surrounding items. And sometimes it makes room for existing items even if column or row values are missing. It will make a best guess.

For example, if you specified only ***2 columns*** with ***grid-template-columns*** set to ***100px*** ***160px*** and ***grid-template-rows*** set to **25px** as shown in next example… but you actually have 4 items in the grid container CSS grid will then ***automatically*** decide how the new row should behave… even if it was not ***explicitly*** specified by you.

***Let’s take a look:***

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1oPUSOtMa2lvrLLB9WBIyfw.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1oPUSOtMa2lvrLLB9WBIyfw.png)

Here **grid-template-columns** was set to **100px** and **160px**. And **grid-template-columns** was set to **25px**. However, because there are 4 items in the container, CSS grid made the decision to extend them into an implicitly created space. Notice that the columns in this new implicit row **automatically inherited** the row height from previously specified **grid-template-rows** property, even though it was not explicitly specified. From now on in this tutorial whenever you see blue grid items it means CSS grid arranged them automatically. Sometimes they are called ***implicitly*** specified items.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1--L-kr3Mx5VrsX4uP5hstA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1--L-kr3Mx5VrsX4uP5hstA.png)

In this case we only have 3 items. There isn’t anything CSS grid can do about it so the item is left blank.

This phenomenon can be also observed when you make items span across multiple rows or columns (similar to ***rowspan*** and ***colspan*** in a <***table***>.)

Spanning multiple rows or columns with **grid-column-start**, **grid-column-end**, **grid-row-start** and **grid-row-end** will produce implicit alignment for any items that fall outside. More on this in just a moment.

***An observation:*** All in all — *with default gap values* — CSS grid behaves a lot like some type of a <**table**> that supports implicit items for “leftover” cells:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/10Vt60CwXmozrkinSywoeWw.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/10Vt60CwXmozrkinSywoeWw.png)

Although the rules are strikingly similar let’s consider that only an observation… *CSS grid* is a lot more capable than mere mortal </**table**>.

Let’s take a look at the rest of CSS grid capabilities to find out the differences.

## grid-auto-rows

This property can be used to tell CSS grid to use a specific height for automatic (implicitly created) rows.

Instead of inheriting from **grid-template-rows** we can tell CSS grid to use a specific height for all implicit rows that fall outside of your definitions.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1gEbWQtd9zkFikP27dpNnAQ.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1gEbWQtd9zkFikP27dpNnAQ.png)

You can specify a different value for implicitly created columns or rows.

Bear in mind — of course — you can still set all of the values explicitly yourself:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1PLdYEyTDwx-Bf7VOm6fceA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1PLdYEyTDwx-Bf7VOm6fceA.png)

Explicitly specifying dimensions of all rows and columns.

In a way CSS grid’s **grid-auto-flow: column** invites Flex-*like* functionality:

You can make your CSS grid behave similar to Flex by overwriting its **grid-auto-flow** property’s default value of row to **column**. Note that here in this example we also used **grid-auto-columns: 25px** to determine the width of consecutive columns. This works in the same way as **grid-auto-rows** in one of the previous examples except this time the items are stretched horizontally.

## Automatic Column Cell Width

CSS grid is excellent for creating traditional website layouts with two smaller columns on each side. There is an easy way to do this. Simply provide ***auto*** as a value to one of the widths in your **grid-template-column** property:

This is what happens with **grid-template-columns: 100px auto 100px**

Your grid will span across the entire width of the container or the browser.

As you can see already CSS grid offers a wide variety of properties to help you get creative with your website or application layout! I really like where this is going so far.

## Okay… but what about the gaps…

Dammit, those ***gaps*** again.

We already talked about the gaps. Mostly the fact that they cover the space between *columns* and *rows*. But we haven’t talked about actually setting them:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1BVoHZA8MQ4m92_aLkaAHPQ.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1BVoHZA8MQ4m92_aLkaAHPQ.png)

grid-column-gap is used to specify vertical gaps of equal size between all columns in your CSS grid.

I intentionally left the horizontal gaps clasped to their default value of 0.

That’s because I just wanted to provide a few visually descriptive diagrams that demonstrate some potential layouts.

I can already envision a Pinterest-like design with multiple columns using the setup above.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1CUE81pb2u6qI382r5qzH7w.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1CUE81pb2u6qI382r5qzH7w.png)

Likewise, using grid-row-gap property we can set horizontal gaps for the entire grid.

This is the same thing, except with horizontal gaps.

Using **grid-gap** property we can set *gaps* in both dimensions at the same time:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1IW8gjeNTKl6_JBCK8W9EQQ.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1IW8gjeNTKl6_JBCK8W9EQQ.png)

It is possible to set the gaps on entire CSS grid by using short-hand property grid-gap. But this means that gaps in both dimensions will be set to the same value. In this example it is 15px.

And finally… you can set gaps individually for each of the two dimensions.

The next 3 diagrams were created to demonstrate the different possibilities made possible by CSS grid that can be useful in various cases.

Simply use **grid-column-gap: 42px** and **grid-row-gap: 15px**

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1IR3pB5R9Md2_QFcMuEeJIA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1IR3pB5R9Md2_QFcMuEeJIA.png)

Here gaps are set individually per row and column which allows for varied column design.

In the example above wide column gaps are used. You can probably use this strategy for crafting ***image galleries*** for wide-screen layouts.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1QNQtgyv0Cg7mp1lP8886Gw.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1QNQtgyv0Cg7mp1lP8886Gw.png)

Here is the same thing as the previous example. Except we’re using wider row gaps.

I really don’t see much use for the layout setup above. But it’s nice to know that it’s one of the possibilities here.

One thing I was disappointed about was the lack of support for the ability to create ***varied* gap sizing within the same dimension**. I think this is the most daunting limitation of CSS grid. And I hope in the future it gets fixed.

The following layout cannot be created using CSS grid:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/14H-ANrYdiBIaEaLaaBnJ-A.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/14H-ANrYdiBIaEaLaaBnJ-A.png)

Varied gap sizing is currently (April 14, 2018) not a possibility with CSS grid.

I’ve been suggested to use columns instead of gaps to achieve this function, every time I bring this up on my Twitter feed.

It might work but I don’t think that in 2018 we ***should*** have to descend to what essentially is a ***CSS hack*** in a situation for which there isn’t a good reason to exist in the first place.

# ***fr* — Fractional Unit — for efficiently sizing the remaining space.**

One recent addition to CSS language is the ***fr*** unit.

The ***fr*** units can be used on things other than CSS grid. But in combination with one they are magical for creating layouts with unknown screen resolution… and still preserve proportion ***without thinking in percent***.

The ***fr*** unit is similar to percentage values in CSS (25%, 50%, 100%…etc) except represented by a fractional value (0.25, 0.5, 1.0…)

But although it could be **1fr** is not always 100%. The fr unit automatically dissects ***remaining space***. The easiest way to demonstrate this is by following diagrams.

Here is a basic example of using ***fr*** units:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1h1ZUIjppm0-xm2XvsrCBsg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1h1ZUIjppm0-xm2XvsrCBsg.png)

An example of using the fr CSS unit.

This is great news for intuitive designers.

**1fr** will be ***10/1*** of **10fr** regardless of how much space 10fr takes up.

It’s all relative.

Using **1fr** to define 3 columns produces columns of equal width.

Using **1fr** to define 3 columns produces columns of equal width.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1rgKTxgSuh8oWovjECx7WSg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1rgKTxgSuh8oWovjECx7WSg.png)

You can also use fractions.

Relative to ***1fr*** ***0.5fr*** is exactly half of ***1fr***.

These values are calculated relative to the parent container.

Can you mix percentage values with ***1fr***? Of course you can!

The example above demonstrates mixing **%** units with ***fr***. The results are always intuitive and produce the effect you would expect.

Fractional **fr** units are relative to themselves within some parent container.

Using ***fr*** units and increasing column gaps at the same time will produce the following result. I just wanted to include this here to demonstrate that ***fr*** units will be affected by gaps too:

5 different CSS grids used here to demonstrate how we should be mindful of the gaps when designing with **fr** units.

And just to be complete you can use ***fr*** units to create something like this:

A skewed chess board created using **fr** units to determine both **row** and **column** dimensions.

Although I don’t know where you would require such a dinosauric layout it clearly demonstrates how ***fr*** units can affect both rows and columns.

## Repeating Values

CSS grid allows the use of **repeat** property value.

The repeat property takes two values: ***times*** to repeat and ***what*** to repeat.

> repeat(times, …what);
> 

At its basic this is how it works:

Here we’re using **grid-template-columns** with repeat and without repeat to produce exactly the same effect.

Here **grid-template-columns** are provided two different sets of value to produce the same effect. Obviously **repeat** saves a lot of hassle here.

> Final verdict: to save yourself from redundancy in cases where your grid must contain repetitive dimension values use repeat as a remedy.
> 

The ***repeat*** property can be *sandwiched* between other values:

```
grid-template-columns: 50pxrepeat(3, 15px 30px) 50px;
```

**grid-template-columns:** 50px **repeat(3, 15px 30px)** 50px

In this example we repeat a section of two columns **15px 30px** for **3** times in a row. I mean in a column. Ahh! You know what I mean.

## Spans

Using CSS grid spans you allow your items to stretch across multiple rows or columns. This is a lot like ***rowspan*** and ***colspan*** in a <***table***>.

We will create a grid using ***repeat*** to avoid redundant values. But it could have been created without it — anyway, let’s make it our specimen for this section.

When we add ***grid-column: span 3*** to item ***#4*** a somewhat unexpected effect has occurred:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1D0OzUQ5UudC7OZtVphLO1Q.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1D0OzUQ5UudC7OZtVphLO1Q.png)

Using grid-column span 3 to take up 3 columns. However, CSS grid makes a decision to remove some of the items, because the “spanned” item cannot fit into suggested area.

In CSS grids ***spans*** can also be used to cover multiple rows. And if it so happened that the column is now greater in height than the height of the grid itself the CSS grid adapt itself to this:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1S4MkZ-ivrgCiQVoGHtmr7Q.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1S4MkZ-ivrgCiQVoGHtmr7Q.png)

CSS grid is adapting itself in several cases where items go beyond Grid’s parent container.

You can also span across multiple rows and columns at the same time. I created this other minimalistic example just to quickly demonstrate limitations, even though in most cases this will probably not happen:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1xhOUDdL7HMenB-Sj9ubhsg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1xhOUDdL7HMenB-Sj9ubhsg.png)

CSS grid fills in the blanks.

Pay attention to how CSS grid adapts to the items around spans that cover multiple rows and columns. All of the items still remain in the grid but intuitively wrap around other spanned items.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1FClp4lVp5qsIi1wxOXAAbA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1FClp4lVp5qsIi1wxOXAAbA.png)

When I tried to break the layout with a large span I ended up with the following case that demonstrates the key limitations of CSS grid:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1A7DhZC0JhSgkXL-T0SW_6w.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1A7DhZC0JhSgkXL-T0SW_6w.png)

CSS grid replaces potential item cells with empty space in two distinct situations.

But it’s still a lot like a <***table***>. See my other ***[CSS grid vs table](https://medium.com/@js_tut/new-things-css-grid-brings-to-the-table-e465cb5d2841)*** tutorial where I show you the frightening similarities.

However… there is a solution.

## Start and End

So far we used CSS grid ***spans*** to create *multi-column* and *multi-row* items that occupy a ton of space. But… CSS grid has another much more elegant solution to solve the same problem.

The **grid-row-start** and **grid-row-end** properties can be used to define the starting and ending point of an item on the grid Likewise, their column equivalents are **grid-column-start** and **grid-column-end**. The are also two short-hand properties: ***grid-row***: 1/2 and ***grid-column***: 1/2.

These work an a slightly different way than ***spans***.

With **-start** and **-end** properties, you can physically move your item to another location in the grid. Let’s take a look at this minimalist example:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Rg2VrFkAAiZSmjNvgvpv-g.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Rg2VrFkAAiZSmjNvgvpv-g.png)

Using CSS grid’s **grid-row-start** and **grid-column-start** on an item (first item in this example) you have the ability to *physically move an item* within your grid to another location!

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Gaf0_LQb7gJqxeCv2vBExA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Gaf0_LQb7gJqxeCv2vBExA.png)

Here we’ve taken **item 8** and (redundantly) specified its location using **grid-row-start** and **grid-column-start**. Notice however, this alone has no effect on item 8, because item 8 is already positioned at that location on the grid anyway. However, by doing this you can achieve span-like functionality if you also specify an ending location using **grid-column-end** and **grid-column-end**.

Interestingly, designers of CSS grid have decided for the direction of the span vector to be insignificant. The span is still created within the specified area regardless of whether starting or ending points are provided in reverse order:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1wCnoGAFlpAOPuaxsJWR6YA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1wCnoGAFlpAOPuaxsJWR6YA.png)

Specifying item span regardless of the direction of the start/end points produces the same results.

Let’s consider this **6** x **4** CSS grid. If you explicitly specify an items’s column end position that goes outside the number of specified columns (>=7) you will experience this wonky effect:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1fXWqDHOjF6DEPp6PSR5ZXA.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1fXWqDHOjF6DEPp6PSR5ZXA.png)

Making column width of an item greater than the original number of columns specified in the CSS grid.

In this case CSS grid will adapt the resulting layout of your grid to what you see in the example above. It’s usually a good idea to design your layouts by being mindful of grid’s boundaries to avoid these types of scenarios.

## **Start and End’s Shorthand**

You can use the shorthand properties **grid-row** and **grid-column** to same effect as above using **/** to separate values. Except instead of providing an end value, it takes ***width*** or ***height*** of the span:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/16UjWCnenzjnLUUJaeHvPXg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/16UjWCnenzjnLUUJaeHvPXg.png)

We can use / character for this short-hand syntax.

What if we need to reach the absolute maximum boundary of the grid?

Use **-1** to extend a column (or row) all the way to the end of CSS grid’s size when number of columns or rows is unknown. But be mindful of any implicit items (16, 17) slipping away from the bottom of the grid:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/19WPQXCItrCTUogado7W4Kw.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/19WPQXCItrCTUogado7W4Kw.png)

Using negative -1 value to count from right-most gap to left.

Then I tried to do the same with rows, but the results were more chaotic, depending on which combinations of values I provided. I know there are other ways of using **/** but for the sake of clarity I want to keep things simple.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1iTtwRYoKEimJXTaSewGa8g.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1iTtwRYoKEimJXTaSewGa8g.png)

I only used 10 items in this example. CSS grid seems to gracefully resize itself.

When I was experimenting with rows to do the same thing, it seems like **4** in **grid-column:** 2/**4** had to be changed to 2/**6**… but only if **grid-row:** 2/**-1** was specified.

That puzzled me a bit. But I guess I still have a lot of learning to do on how **/-**separated values work.

What I found out though is that juggling around values here produced results that cannot be easily documented using visual diagrams.

Well, at least we get the basic idea here. You can extend either column or row all the way to the maximum boundary using **-1**. How one affects the other takes a bit of practice to figure out in some specific cases.

We can expand on this a bit. CSS grid has a secondary coordinate system, so to speak. And because it doesn’t matter which direction you use to make cross-column and cross-row spans you can use negative values:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1jtB-0ml47Cf7KPrHkxWlgg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1jtB-0ml47Cf7KPrHkxWlgg.png)

Using negative values to specify column and row’s start and end, we can create the same span from previous examples, since CSS grid is coordinate system agnostic. You can use both positive and negative numbers!

As you can see CSS grid coordinate system is pretty flexible.

## Content Align Within CSS Grid Items

Let’s say you’ve gone to the great lengths mastering CSS grid item *spans*. You crossed the seas of implicitly generated rows and columns. Now you’re curious to see what else is in store for you.

Good news for you then.

As a web designer, I’ve for a long time craved multi-directional float. I wanted to be able to float in the middle and on any corner of the container.

This functionality is only limited to CSS grids’ **align-self** and **justify-self** and does not appear to work on any other HTML element. If your entire site’s layout is built using a CSS grid then it solves a lot of issues associated with corner and center element placement.

# align-self

An example of using **align-self** and **justify-self** properties. The difference between the 9 squares is the combination of **start** and **end** values provided to the said properties to produce any of the results depicted above. I won’t mention all of these combinations here, because it’s quite intuitive.

**VERTICAL:** Use **align-self: end** to align the *content* to the bottom of the item. Likewise, **align-self: start** will make sure content sticks to the upper border.

**HORIZONTAL:** Use **justify-self: start** (or **end**) to justify your content **left** or **right**. In combination with **align-self** you can achieve placement depicted on any of the above examples.

Just to finalize this discussion here is how **align-self** affects a slightly more complex situation — *one we’ve taken a look at before in this tutorial*:

Using **align-self** it is possible to align the item’s content with **start**, **center** and **end** values.

You can use values **start, center** *and* **end**.

Note, however there *aren’t* **top** and **bottom** values for **align-self**.

# justify-self

Another property that does the same thing but horizontally is **justify-self**:

CSS grid item property **justify-self** in action using **unset**, **start**, **center** and **end** values.

You can use **start**|**left** *or* **end**|**right** values interchangeably here.

# Template Areas

Template areas provide a way to refer to an isolated part of your grid by a predefined name. This name cannot include spaces. Use **-** instead.

Each set of row names is enclosed in double quotes. You can further separate these sets of row names either by a line break or by space to create columns as shown in the example below.

Although only 5 items are present template are names can logistically occupy places not yet filled with items:

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1pzbYT2qXsiu9wGSdBID8_Q.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1pzbYT2qXsiu9wGSdBID8_Q.png)

Example of specifying template areas with grid-template-areas property.

Similar principle to specifying row and column size is followed here to name all of the areas in the grid. Just separate them by space or tab.

This syntax simply allows us to intuitively name our template areas.

But things get a lot more convenient when you start *combining* areas with the same name across multiple containers. Here I named 3 items in the left column Left and 3 items in the right column Right. CSS grid template areas automatically combined them to occupy the same space by name.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1CH-r-jAT1VSPGBU-8ZP1Eg.png](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1CH-r-jAT1VSPGBU-8ZP1Eg.png)

Spanning template areas across multiple grid “cells.” Simply name your columns and rows, and adjacent blocks will “merge” into larger areas. Just make sure to keep them rectangular!

It’s important to make sure that areas consist of items aligned into larger ***rectangle*** areas. ***Doing Tetris blocks here will not work.*** Straying from the rule of always keeping your areas rectangular is likely to break the CSS grid and/or produce unpredictable outcome.

# Naming Grid Lines

Working with numbers (and negative numbers) can become redundant over time especially when dealing with complex grids. You can name grid lines with whatever you want using **[***name***]** brackets right before size value.

To name the first grid line you can: **grid-template-column: [*left*] 100px** Likewise for rows it is: **grid-template-row: [*top*] 100px**

You can name multiple grid lines. The [] brackets are inserted at an intuitive place in the set. Exactly where the grid line (a.k.a. *gap*) would appear:

**grid-template-columns:** **[*left*] 5px 5px [middle] 5px 5px [right]**

Now you can use the names ***left***, ***middle*** and ***right*** to refer to your grid lines when creating *columns* and *rows* that need to reach that area:

Instead of using numbers it is possible to name and refer to lines in between grid’s cells as values to your properties **grid-template-columns** and **grid-template-rows**. Note how each span in the diagram refers to named lines and not the gap’s numbers. You can use any name you want.

Naming gap lines creates a more meaningful experience. It’s a lot better to think of the middle line as ***center*** (or ***middle***) instead of ***4***. This tutorial covered almost everything there is to CSS grid using visual diagrams.

In conclusion… **remember…**

# The music is not in the notes, but in the silence between — Wolfgang Amadeus Mozart

This seems to be true of CSS grid also. And so many other things!

I spent the entire last 3 weeks drawing **diagrams** representing pretty much every single thing you can possibly do with*CSS grid*. And you’ve just looked at (*and hopefully learned from*) them.

Of course I assume ***the possibility I missed one or two things***. And I will be glad for anyone in the community to point it out so I can improve this article.

Thanks for your time reading — aaand I will see you in my next Medium tutorial. I am currently working on visual diagrams for the entire **webkit** set.

![The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Iy0nsaECkxEPFPNkYAtLrA.jpeg](The%20Complete%20CSS%20Grid%20Tutorial%20Here%E2%80%99s%20a%20list%20of%20my%20f454e4ba0beb4e8a8e388e2fa1673709/1Iy0nsaECkxEPFPNkYAtLrA.jpeg)

CSS Visual Dictionary.

***CSS*** — ***Visual Dictionary***

***[Click here](http://www.learningcurvebook.net/go/cssvd)*** for the discount page.

***What is this?*** A CSS desk reference to remind you of *many common CSS properties* with the accompanying *visual diagrams* explaining how they work — ***in a similar way as demonstrated in this tutorial.***

***Interested?*** [Grab your copy here.](http://www.learningcurvebook.net/go/cssvd) (offered at a discount to my current Medium readers)