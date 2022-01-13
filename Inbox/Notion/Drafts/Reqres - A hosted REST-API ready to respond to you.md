# Reqres - A hosted REST-API ready to respond to your AJAX requests

Source: Website
Status: Unprocessed
URL: https://reqres.in/

## Test your front-end against a real API

## Give it a try

```
{
    "page": 2,
    "per_page": 6,
    "total": 12,
    "total_pages": 2,
    "data": [
        {
            "id": 7,
            "email": "michael.lawson@reqres.in",
            "first_name": "Michael",
            "last_name": "Lawson",
            "avatar": "https://reqres.in/img/faces/7-image.jpg"
        },
        {
            "id": 8,
            "email": "lindsay.ferguson@reqres.in",
            "first_name": "Lindsay",
            "last_name": "Ferguson",
            "avatar": "https://reqres.in/img/faces/8-image.jpg"
        },
        {
            "id": 9,
            "email": "tobias.funke@reqres.in",
            "first_name": "Tobias",
            "last_name": "Funke",
            "avatar": "https://reqres.in/img/faces/9-image.jpg"
        },
        {
            "id": 10,
            "email": "byron.fields@reqres.in",
            "first_name": "Byron",
            "last_name": "Fields",
            "avatar": "https://reqres.in/img/faces/10-image.jpg"
        },
        {
            "id": 11,
            "email": "george.edwards@reqres.in",
            "first_name": "George",
            "last_name": "Edwards",
            "avatar": "https://reqres.in/img/faces/11-image.jpg"
        },
        {
            "id": 12,
            "email": "rachel.howell@reqres.in",
            "first_name": "Rachel",
            "last_name": "Howell",
            "avatar": "https://reqres.in/img/faces/12-image.jpg"
        }
    ],
    "support": {
        "url": "https://reqres.in/#support-heading",
        "text": "To keep ReqRes free, contributions towards server costs are appreciated!"
    }
}
```

## It’s all in the details

- 
    
    Which means 99.99% Uptime SLA.All you need is the base URL, and you're away: https://reqres.in/api/The API is CORS enabled, so you can make requests right from the browser, no matter what domain, or even from somewhere like JSFiddle or JSBin.
    
- 
    
    A generic API that conforms to REST principles and accepts a content type of application/jsonAny endpoint that contains "<resource>" can be substituted with anything you supply, ie. "products", "accounts", etc..the API will just respond with various Pantone colours.
    

## Getting started

jQuery

If you, for example, want to create a fake user:

```
$.ajax({
    url: "https://reqres.in/api/users",
    type: "POST",
    data: {
        name: "paul rudd",
        movies: ["I Love You Man", "Role Models"]
    },
    success: function(response){
        console.log(response);
    }
});

```

For which the response to this request will be...

```
{
    "name":"paul rudd",
    "movies[]":[
        "I Love You Man",
        "Role Models"
    ],
    "id":"243",
    "createdAt":"2014-10-18T12:09:05.255Z"
}

```

You can see that the API has sent us back whatever user details we sent it, plus an id & createdAt key for our use.

Native JavaScript

If you've already got your own application entities, ie. "products", you can send them in the endpoint URL, like so:

```
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://reqres.in/api/products/3", true);
xhr.onload = function(){
    console.log(xhr.responseText);
};
xhr.send();

```

It would be impossible for Reqres to know your application data, so the API will respond from a sample set of Pantone colour data

```
{
    "data":{
        "id":3,
        "name":"true red",
        "year":2002,
        "pantone_value":"19-1664"
    }
}

```

It's entirely possible to get sample data into your interface in seconds!

## Still don't really get it...

- 
    
    **Reqres is a *real* API**
    
    Reqres simulates real application scenarios. If you want to test a user authentication system, Reqres will respond to a successful login/register request with a token for you to identify a sample user, or with a 403 forbidden response to an unsuccessful login/registration attempt. A common front-end scenario that's easily forgotten is loading states, which can be easily simulated through Reqres by appending ?delay=<a number of seconds> to any endpoint URL, which will delay the API response time. Animated loading GIFs & SVGs at the ready!
    
- 
    
    **Technical demos and tutorials**
    
    If you're trying to demonstrate a front-end (JavaScript-based) concept, you don't really want the hassle of setting up an API, or even a server (especially during a live workshop or demo). You can just write your HTML, CSS & JavaScript as usual and send Reqres AJAX requests, which will respond with the expected response codes and output.
    
- 
    
    When prototyping a new interface, you just want an API *there*, with minimal setup effort involved. Normally, I'd point people, who aren't too familiar with backend programming, to [Sailsjs](http://sailsjs.org/) which can auto-generate a REST-API for you from the command line. However, you will need Node.js installed and some familiarity of how Node.js works. If that sounds like too much hassle and way too daunting, Reqres is just a URL. Sending it an AJAX request is step 1...there is no step 2.
    

## Peace of mind

It might seem **pretty weird** to be sending your data to a 3rd party API, but I can assure you, Reqres **does not store any of your data** at all. Once you send it to us, we just send it straight back...and then it's gone!

## Support

ReqRes serves nearly **100 million requests each month**, and is provided free-of-charge.

To keep ReqRes free, contributions towards server costs are appreciated!

Selecting either option will redirect you to a hosted Stripe Checkout page to complete payment.

## Advertising

Do you want to advertise your jobs/tools/software/cats through Reqres to millions of developers every week? Click for more [info [pdf]](https://www.dropbox.com/s/2w7gaeydx02qs40/Reqres_Advertising_Proposal.pdf?dl=0) on the ads. [Contact](mailto:hello@benhowdle.im) for pricing and questions.

## Looking for pro features?