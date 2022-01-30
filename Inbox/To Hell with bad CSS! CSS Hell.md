# To Hell with bad CSS! | CSS Hell

Source: Website
Status: Unprocessed
URL: https://csshell.dev/

![https://csshell.dev/src/images/csshell_logo.png](https://csshell.dev/src/images/csshell_logo.png)

---

![csshell_logo.png](To%20Hell%20with%20bad%20CSS!%20CSS%20Hell%2046586151002f4023a6102103bfafd2a3/csshell_logo.png)

1.  
    
    I often run into the problem where I see the same class name being reused on different parts and context of the website, but when 1 out of the 3 properties don't match with the design, developers just use inline styling to override the desired rule.
    
    ```
    .primary-text {
      color: #000;
      font-family: "Open Sans";
      line-height: 1.2;
    }
    ```
    
2.   
    
    ## [Let's talk about units](https://csshell.dev/posts/lets-talk-about-units/)
    
    There is a life beyond pixels and percentages. Using `px` units is fine in certain cases, the real mistake is using absolute instead of relative units.
    
    ```
    p {
      font-size: 16px;
      line-height: 20px;
      margin-bottom: 8px;
    }
    ```
    
3.   
    
    ## [font-variation-misfortune](https://csshell.dev/posts/font-variation-misfortune/)
    
    Variable fonts are awesome, but unnecessary usage of `font-variation-settings` will eventually break your styles.
    
    ```
    .bold {
      font-variation-settings: 'wght'700;
    }
    
    .italic {
      font-variation-settings: 'ital'1;
    }
    ```
    
4.   
    
    ## [Overspecified specificity](https://csshell.dev/posts/overspecified-specificity/)
    
    Specificity determines, which CSS rule is applied by the browsers. Developers often write overly specific selectors just to be 10000% sure their rules will *rule*.
    
    ```
    div#my-popup div span.my-radiocheckbox-label-text {
      color: #666;
    }
    
    #some-id .label {
      color: #111 !important;
    }
    ```
    
5.   
    
    ## [font-family everywhere!](https://csshell.dev/posts/font-everywhere/)
    
    Specifying the primary font for almost every selector is not a good approach, yet I often run into this issue.
    
    ```
    .my-class-1 {
      font-family: Roboto;
    }
    
    .my-class-2 {
      font-family: Roboto;
    }
    
    p {
      font-family: Roboto;
    }
    
    .my-class-3 {
      font-family: Roboto;
    }
    
    footer {
      font-family: Roboto;
    }
    ```