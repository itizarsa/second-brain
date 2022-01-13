# The Complete CSS Flex Box Tutorial | by JavaScript Teacher | Medium

Source: Article
Status: Unprocessed
URL: https://jstutorial.medium.com/the-complete-css-flex-box-tutorial-d17971950bdc

![https://miro.medium.com/focal/1029/542/51/49/1*3D0WwPIWz_hWmGH7j3qcxw.png](https://miro.medium.com/focal/1029/542/51/49/1*3D0WwPIWz_hWmGH7j3qcxw.png)

---

Much like ***[CSS Grid](https://jst.hashnode.dev/css-grid-tutorial)** (my other tutorial)* **Flex Box** is quite complex because it consists of not one but *two* element types: The ***container*** & ***items***.

Also see this [CSS Flex Tutorial](https://semicolon.dev/tutorial/css/flex-tutorial) on Semicolon.

When I started to learn Flex, I wanted to see *everything* it was capable of. But, I wasn’t able to find a *thorough* tutorial showing examples of *all Flex properties*. So, I created these diagrams with Flex from the bird’s eye view.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1AhLZj_q8tvCuFraEKSG6gg.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1AhLZj_q8tvCuFraEKSG6gg.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1xAPNrU9sKijsJnMJOTyUBA.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1xAPNrU9sKijsJnMJOTyUBA.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/15DdP910Q6Oz6rqNfnpHGcg.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/15DdP910Q6Oz6rqNfnpHGcg.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1IMU7WQ7P4xepIHZGlp8ZCA.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1IMU7WQ7P4xepIHZGlp8ZCA.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1LDRJvglhmxOIZHsDQe4A4A.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1LDRJvglhmxOIZHsDQe4A4A.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1oDZ0LHJR7NBuMg0wEJihhQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1oDZ0LHJR7NBuMg0wEJihhQ.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1XGm7JEbXLe3e9_XAdgZDYw.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1XGm7JEbXLe3e9_XAdgZDYw.png)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1pUE3gXzsGgHmgIdxIAkX1Q.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1pUE3gXzsGgHmgIdxIAkX1Q.png)

> That’s everything Flex is capable of. But… let’s go over each diagram individually with comments. By the end of this Flex tutorial you should be up to speed with pretty much the complete picture of what it can do.
> 

# Flex

Flex is a set of rules for automatically stretching multiple columns and rows
 of content across parent container.

## **display:flex**

Unlike many other CSS properties, in Flex you have a main container and
 items nested within it. Some CSS flex properties are used only on the parent. Others only on the items.

You can think of a flex element as a parent container with **display:flex**. Elements placed inside this container are called items. Each container has a **flex-start** and **flex-end** points as shown on this diagram.

## Main-axis and Cross-axis

While the list of items is provided in a linear way, Flex requires you to be
 mindful of rows and columns. For this reason, it has two coordinate axis. The
 horizontal axis is referred to as Main-Axis and the vertical is the Cross-Axis.

To control the behavior of content’s width and gaps between that stretch
 horizontally across the Main-Axis you will use justify properties. To control
 vertical behavior of items you will use align properties.

If you have 3 columns and 6 items, a second row will be automatically created
 by Flex to accommodate for the remaining items.

If you have more than 6 items listed, even more rows will be created.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1T1x2OolGzQWb2GZB688_Vw.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1T1x2OolGzQWb2GZB688_Vw.png)

Flex items equally distributed on the **Main-Axis**. We’ll take a look at the properties and values to accomplish this in just a moment.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/16Cd-JIcbtJ7Kfy7kul_2Dw.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/16Cd-JIcbtJ7Kfy7kul_2Dw.png)

You can determine the number of columns.

How the rows and columns are distributed inside the parent element is determined by CSS Flex properties **flex-direction**, **flex-wrap** and a few others that will be demonstrated throughout the rest of this flex tutorial.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/12kaamZDI0E_U1Qu7i3UcEA.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/12kaamZDI0E_U1Qu7i3UcEA.png)

Here we have an arbitrary n-number of items positioned within a container. By default, items stretch from left to right. However, the origin point can be reversed.

## Direction

It’s possible to set direction of the item’s flow by reversing it.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1KsOv5LJtQidXmbXaHZnDeQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1KsOv5LJtQidXmbXaHZnDeQ.png)

flex-direction:row-reverse changes direction of the item list flow. The default is row, which means flowing from left to right, as you would expect!

## Wrap

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1NgLbEh2kyt6pADq9q6Eq9Q.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1NgLbEh2kyt6pADq9q6Eq9Q.png)

flex-wrap:wrap determines how items are wrapped when parent container runs out of space.

## Flow

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1JwdJjzh906U62y5ryUBPBA.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1JwdJjzh906U62y5ryUBPBA.png)

**flex-flow** is a short hand for **flex-direction** and **flex-wrap**allowing you to specify both of them using just one property name.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1YwvnvHBj4Gs9OnNCrA0TCQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1YwvnvHBj4Gs9OnNCrA0TCQ.png)

**flex-flow:row wrap** determines **flex-direction** to be **row** and**flex-wrap** to be **wrap**.

flex-flow:row wrap-reverse;

flex-flow:row wrap; justify-content: space-between;

flex-flow:row-reverse wrap;

flex-flow:row-reverse wrap-reverse;

flex-flow:row wrap; justify-content: space-between;

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1DCpWkqPeSuiDMP-xTha5nQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1DCpWkqPeSuiDMP-xTha5nQ.png)

The direction can be changed to make the Cross-Axis primary.

When we change flex direction to column, the **flex-flow** property behaves in
 exactly the same way as in previous examples. Except this time, they follow
 the vertical direction of a column.

## justify-content

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1V1bfijm-RCdlxcZhP7tYwA.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1V1bfijm-RCdlxcZhP7tYwA.png)

I received a lot of requests to clarify the example above. So I created this animation. The original piece from which the diagram was crafted:

Animated **justify-content.**

Hope this clears the fog a bit.

**flex-direction:row; justify-content: flex-start |flex-end |center|space-between |space-around |stretch |space-evenly**. In this example we’re using only 3 items per row.

There is no limit on the number of items you wish to use in flex. These diagrams only demonstrate the behavior of items when one of the listed values is applied to **justify-content** property.

The same **justify-content** property is used to align items when **flex-direction** is column.

## Packing Flex Lines (according to Flex specification)

Flex specification refers to this as ”***packing flex lines***.” Basically, it works just like the examples we’ve seen on the previous few pages. Except this time, note that the spacing is between whole sets of items. This is useful when you want to crate gaps around a batch of several items.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1FwZpPNEdh7TjVoc8XU9rfQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1FwZpPNEdh7TjVoc8XU9rfQ.png)

***Packing Flex Lines*** (continued.) But now with **flex-direction** set to **column**.

## **align-items**

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1ClFep05U_OkI3uA4fcDibQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1ClFep05U_OkI3uA4fcDibQ.png)

**align-items** controls the align of items horizontally, relative to the parent container.

## flex-basis

**flex-basis** works similar to another CSS property: min-width outside of flex. It will expand item’s size based on inner content. If not, the default basis value will be used.

## flex-grow

**flex-grow**, when applied to an item will scale it relative to the sum of the size of all other items on the same row, which are automatically adjusted according the the value that was specified. In each example here the item’s flex-grow value was set to 1, 7 and (3 and 5) in the last example.

## flex-shrink

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1JgkuJjc2Ile0Hkef1pMyfQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1JgkuJjc2Ile0Hkef1pMyfQ.png)

**flex-shrink** is the opposite of **flex-grow**. In this example value of 7 was used to ”shrink” the selected item in the amount of time equal to 1/7th times the size of its surrounding items — which it will be also automatically adjusted.

When dealing with individual items, you can use the property
 flex as a shortcut for **flex-grow**, **flex-shrink** and **flex-basis** using only
 one property name.

## order

Using **order** property it’s possible to re-arrange the natural order of items.

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1BdoGsWOIFJ3IGW7j193W2Q.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1BdoGsWOIFJ3IGW7j193W2Q.png)

## justify-items

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1nd0NlLxeeatSX1j4dfFblQ.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/1nd0NlLxeeatSX1j4dfFblQ.png)

One last thing for those who are looking to use **[CSS Grid](https://medium.com/@js_tut/css-grid-tutorial-filling-in-the-gaps-c596c9534611)**together with Flex Box**…** *CSS grid’s* **justify-items** is similar to Flex’s ***justify-content***. (The properties described in the above diagram will not work in Flex, but it’s pretty much the grid’s equivalent for aligning cell content.)

![The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/13D0WwPIWz_hWmGH7j3qcxw.png](The%20Complete%20CSS%20Flex%20Box%20Tutorial%20by%20JavaScript%20T%20a4502c30be5f47e9a9db9de698425e17/13D0WwPIWz_hWmGH7j3qcxw.png)

## CSS Visual Dictionary

Follow me on **[Instagram](https://www.instagram.com/javascriptteacher/)** for a quick hit of JavaScript.

You can follow me on **[Facebook](https://www.facebook.com/javascriptteacher/)** for free coding stuff.

See my other **[comprehensive CSS Grid tutorial](https://medium.com/@js_tut/css-grid-tutorial-filling-in-the-gaps-c596c9534611)** right here on Medium.

Similar [flexbox tutorial](https://semicolon.dev/tutorial/css/complete-css-flex-tutorial) can be found here.