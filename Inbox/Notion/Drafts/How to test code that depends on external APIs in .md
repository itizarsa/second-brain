# How to test code that depends on external APIs in Node.js - LogRocket Blog

Source: Article
Status: Unprocessed
URL: https://blog.logrocket.com/how-to-test-code-that-depends-on-external-apis-in-node-js/

![https://blog.logrocket.com/wp-content/uploads/2021/04/test-code-depends-external-apis-nodejs.png](https://blog.logrocket.com/wp-content/uploads/2021/04/test-code-depends-external-apis-nodejs.png)

---

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-code-depends-external-apis-nodejs.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-code-depends-external-apis-nodejs.png)

Unit testing code that depends on external APIs presents a variety of challenges. Some external APIs are slow, error-prone due to network outages, subject to rate limits, and hard to track because they can change or disappear without notice. Fortunately, these issues are relatively easy to overcome.

In this article, we’ll go over two of the most commonly used patterns for testing code that consumes a third-party API. I’ll demonstrate how to go from a test that calls the external API directly to one that removes the external dependency by:

- Mocking the requests with predefined responses
- Intercepting the requests and persisting their responses for later use

## **Testing code that consumes an external API**

To demonstrate testing code that consumes an external API, we’ll use an example that retrieves a series of posts filtered by user ID provided by [JSON placeholder](https://jsonplaceholder.typicode.com/).

```
// post.jsconst fetch = require('node-fetch');async function getPosts(userId){
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/posts?userId=${userId}`
  );

  if (!response.ok) {
    throw new Error(response.statusText);
  }

  return await response.json();}module.exports = {
  getPosts,};
```

Let’s assume you have a function that calls an external API like the one shown above and yields a JSON response in the following [format](https://jsonplaceholder.typicode.com/posts?userId=1):

```
[
  {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
  },
  {
    "userId": 1,
    "id": 2,
    "title": "qui est esse",
    "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
  }]
```

Now, we’ll write a test that confirms that the returned posts have a `userId` that match the value that was passed to the `getPost()` function. Although I’ve opted to use [Jest](http://jestjs.io/) for this test due to its popularity, the same principles can be applied to other testing frameworks like [Mocha](https://mochajs.org/) or [Jasmine](https://jasmine.github.io/).

```
// post.test.jsconst { getPosts } = require('./post');

test('return a list of posts by a user', ()=> {
  const userId = 1;
  return getPosts(userId).then((data)=> {
    expect(data.length).toBeGreaterThan(0);
    data.forEach((post)=> {
      expect(post).toEqual(
        expect.objectContaining({
          userId,
        })
      );
    });
  });});
```

The above test confirms that the expected data is not empty and that the `userId` in each object matches the argument to the function. The problem with this test is that it calls the real API, which makes it slow to finish because an actual request is being sent over the network. For example, this specific test took over one second to run on my machine.

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/external-api-tst-userid-getpost-function.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/external-api-tst-userid-getpost-function.png)

Although a slow test is probably not a big deal on its own, the whole test suite becomes progressively slower and more brittle when you are running many of these tests, which can be affected by connectivity issues and rate limits.

Additionally, some APIs require authentication or authorization. If it is provided by a paid service, it may grow costly to call the API. For these reasons, it’s important to decouple the tests from the API calls using the strategies described below.

## Manually mocking the HTTP request

Mocking is an approach to unit testing in which external dependencies are replaced with objects that simulate their behavior. This makes it easy to isolate the code that is being tested from its external dependencies and to avoid the negative side effects that result from interactions with an external system. In the case of external APIs, mocking involves intercepting the HTTP request and returning the response that is expected in the real scenario.

The Jest library provides useful [methods](https://jestjs.io/docs/mock-functions) for mocking an external dependency. In this case, we want to mock calls to `fetch` in the `getPosts` function so that it returns a canned response instead of reaching out to the real API. This can be achieved in the test file:

```
// post.test.js
jest.mock('node-fetch');const fetch = require('node-fetch');const getPostResponse = require('./testdata/postResponse');const { getPosts } = require('./post');const { Response } = jest.requireActual('node-fetch');

test('return a list of posts by a user', () => {
  const userId = 1;

  fetch.mockResolvedValue(new Response(JSON.stringify(getPostResponse)));

  return getPosts(userId).then((data)=> {
    expect(data.length).toBeGreaterThan(0);
    data.forEach((post)=> {
      expect(post).toEqual(
        expect.objectContaining({
          userId,
        })
      );
    });
  });});
```

On the first line, the `jest.mock()` method is used to mock the entire `node-fetch` module. This sets each of the module exports to `jest.fn()`, which return `undefined`. With this in place, you can assign the return value of any method exported by `node-fetch` to whatever value you want.

In the snippet above, `fetch` is assigned a return value of a promise that resolves to a predefined response through the `mockResolvedValue()` method. The `jest.requireActual()` helper is necessary here to retain the actual behavior of the `Response` object rather than a mocked version, which does not conform to the original.

The expected response should be placed in a separate file before the test is executed:

```
// testdata/postResponse.jsmodule.exports = [
  {
    userId: 1,
    id: 1,
    title:
      'sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
    body:
      'quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto',
  },
  {
    userId: 1,
    id: 2,
    title: 'qui est esse',
    body:
      'est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla',
  },
  // truncated for brevity];
```

If you run the test again, it won’t call the external API anymore. Instead, it will retrieve the response from the specified file and use it as the resolved value from `fetch` so that the test will still pass:

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-retrieve-response-fetch-resolved-value.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-retrieve-response-fetch-resolved-value.png)

If you want to be certain that you are testing against the canned response, edit one of the fields in the response object so that the test will fail. For example, you can change one of the `userId` fields to `2`. You will get an error like the one shown below:

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-failure-error-message.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/test-failure-error-message.png)

Although mocking can be an effective way to unit test code that depends on external services, it has some flaws.

The mocked response may go out of sync with the real API, which can lead to potentially misleading results. Your tests will succeed, but your function may fail in production if the external dependency changes and the mock remains based on the old version. This is especially likely if there are breaking changes that haven’t been accounted for in the mocked object.

In addition,the amount of maintenance you need to perform on the tests themselves may increase if you overuse mock objects.

Therefore, when using this technique, it is important to stay up to date with any changes in the shape of the data that the API returns. Fortunately, this can be automated with tools like [Nock](https://github.com/nock/nock), which we’ll discuss in the next section.

## Recording, saving, and reusing API responses with Nock

Nock can be used to mock individual API responses in a way similar to how we used `jest.mock()` in the previous section. Like every other Node package, you have to install it first before requiring it in your script:

```
$ yarn add nock -D
```

In the snippet below, Nock is used to intercept a GET request by specifying the host name and request path along with the expected HTTP status code and response body. This allows Nock to intercept the request from `getPosts()` so that the specified response body is returned and tested against.

```
const nock = require('nock');const { getPosts } = require('./post');const getPostResponse = require('./testdata/postResponse');

test('return a list of posts by a user', ()=> {
  const userId = 1;

  nock('https://jsonplaceholder.typicode.com')
    .get(`/posts?userId=${userId}`)
    .reply(200, getPostResponse);

  return getPosts(userId).then((data)=> {
    expect(data.length).toBeGreaterThan(0);
    data.forEach((post)=> {
      expect(post).toEqual(
        expect.objectContaining({
          userId,
        })
      );
    });
  });});
```

Nock has another trick up its sleeve that allows us to save the real response from intercepting an HTTP request for later use; it records the output for an external API request and adds it as a fixture in the initial run. The next time the test is run, the recorded fixture will be used. Here’s how to use it:

```
const nockBack = require('nock').back;const path = require('path');const { getPosts } = require('./post');

nockBack.fixtures = path.join(__dirname, '__nock-fixtures__');
nockBack.setMode('record');

test('return a list of posts by a user', async () => {
  const userId = 1;

  const { nockDone } = await nockBack('post-data.json');

  const data = await getPosts(userId);

  expect(data.length).toBeGreaterThan(0);
  data.forEach((post)=> {
    expect(post).toEqual(
      expect.objectContaining({
        userId,
      })
    );
  });

  nockDone();});
```

Before you run the test, you need to configure the location of the recorded responses through the `fixtures` property. Afterwards, set the [mode](https://github.com/nock/nock#modes) to `record` so that any recorded Nocks are used and missing ones are recorded.

Inside the test function, pass the name of a file to `nockBack` so that the recorded output is saved there. Once the test expectations are asserted, call the `nockDone()` method.

When the test is run for the first time, Nock will send out the actual request to the real API and record the response to a file under `__nock-fixtures__/post-data.json`. On subsequent runs, the recorded response is used instead of hitting the recorded API again.

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/run-test-nock-recorded-response.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/run-test-nock-recorded-response.png)

The main benefit of this approach is that you no longer have to manually mock each HTTP request. This allows you avoid potentially misleading results and unnecessary maintenance. It’s also easy to re-record a fixture by simply removing a previously saved version before running the test.

## Conclusion

Mocking is a handy way to keep your tests fast and deterministic. With mocking, you can remove any coupling with external dependencies so that they are no longer a constraint to the unit under test. Without mocking, it may be difficult to diagnose whether a test failed due to our code or dependencies.

In this article, we considered two approaches to mocking external APIs in a Node.js test suite but only scratched the surface of what is possible using [Jest](https://jestjs.io/docs/) and [Nock](https://github.com/nock/nock) in this regard. They both have very detailed documentation, which are well worth exploring.

Thanks for reading, and happy testing!

## 200’s only Monitor failed and slow network requests in production

Deploying a Node-based web app or website is the easy part. Making sure your Node instance continues to serve resources to your app is where things get tougher. If you’re interested in ensuring requests to the backend or third party services are successful, [try LogRocket](https://logrocket.com/signup/).

[https://logrocket.com/signup/](https://logrocket.com/signup/)

![How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/network-request-filter-2-1.png](How%20to%20test%20code%20that%20depends%20on%20external%20APIs%20in%20%20459b525298054029be2f1ead749e43dd/network-request-filter-2-1.png)

[LogRocket](https://logrocket.com/signup/) is like a DVR for web apps, recording literally everything that happens on your site. Instead of guessing why problems happen, you can aggregate and report on problematic network requests to quickly understand the root cause.

LogRocket instruments your app to record baseline performance timings such as page load time, time to first byte, slow network requests, and also logs Redux, NgRx, and Vuex actions/state. [Start monitoring for free](https://logrocket.com/signup/).