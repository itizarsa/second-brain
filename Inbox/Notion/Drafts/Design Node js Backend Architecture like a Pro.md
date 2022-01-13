# Design Node.js Backend Architecture like a Pro

Source: Article
Status: Unprocessed
URL: https://afteracademy.com/blog/design-node-js-backend-architecture-like-a-pro

![https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/cover-nodejs-backend-architecture-c47d090d46c49208.png](https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/cover-nodejs-backend-architecture-c47d090d46c49208.png)

---

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/career-guidance-web-b6a02dc05f612729.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/career-guidance-web-b6a02dc05f612729.png)

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/cover-nodejs-backend-architecture-6dc14b3a35199ad3.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/cover-nodejs-backend-architecture-6dc14b3a35199ad3.png)

Node.js is a perfect framework for developing backend services. It is also a favorite solution in the industry for applications whose size ranges from an enterprise to a small personal project. But, **in its simplicity lies a big challenge** i.e. to find a better way of writing our application code. In this blog, I am going to take you on a journey to figure out a better solution and in the end, **you will have added my experience to yourself**.

I would like to mention that almost everywhere node application is developed on top of another framework i.e. **Express.js**, which is also **a simple routing solution for http**. Now, the important question is, how to figure out a better way of arranging the files and our codebase, such that the project becomes easy to manage and also incorporate the good programming principles.

From my experience over the **years working on Node.js applications**, I have found the following aspects to be considered for a better solution:

- Type Safety
- Separation of Concern
- Feature Encapsulation
- Better Error Handling
- Better Response Handling
- Better Promise Management
- Robust Unit Tests
- Simple Deployability

To achieve all these aspects in the project, I have iterated a lot over the years and now, I feel that I have found an optimum solution. **My team here at AfterAcademy has open-sourced the backend project architecture for everyone** to get benefit from our experiences.

**This is the GitHub repository for the project:**  [https://github.com/afteracademy/nodejs-backend-architecture-typescript](https://github.com/afteracademy/nodejs-backend-architecture-typescript) .

> You will find the instruction for running this application in the repository README.md and I welcome you to give it a try.
> 

Before we start to explore these topics, let me emphasize one very important aspect of backend development. When we start with a frontend project like React or Express(templates) then **we are tempted to create a unified backend and frontend codebase**. From my experience, I have found the unified codebase becomes very difficult to manage when **the products of a company start to diverse**. Many different websites get developed to cater to these varied use-cases and then **the backend is required to address all of them.**

So, what I recommend is to **keep the backend application independent from any frontend**. The frontend like websites and the mobile app can call the APIs of the common backend for the services. This open-source project [repository](https://github.com/afteracademy/nodejs-backend-architecture-typescript) does the same.

**Now, let me explain each of these aspects in brief.**

### Type Safety

I have seen some critical bugs reported during the application runtime. Most of the time the bug involved calling a function with wrong parameters. Although it can be solved by rigorous unit tests, but let's face it, **we can not assure 100% test coverage and even then 100% cases being considered**. So, it can turn out to be a million-dollar mistake. When **I switched to TypeScript** from plain Javascript then this problem got resolved. Here is an example to demonstrate this:

We have a function in plain Javascript:

```
const calculate = ({ price, discount }) => {
    return price - discount * price;
}

const payment = calculate(100, 0.1);
console.log(payment) // logs NaN
```

This is an error as we called the function with non-supportive parameters. The IDE like vscode was also not able to point out the mistake because intellisense did not work great for Javascript.

Let's see what would have been the result in Typescript:

```
src/server.ts:5:22 - error TS7031: Binding element 'price' implicitly has an 'any' type.
5 const calculate = ({ price, discount }) => {
                       ~~~~~
src/server.ts:5:29 - error TS7031: Binding element 'discount' implicitly has an 'any' type.
5 const calculate = ({ price, discount }) => {
                              ~~~~~~~~
src/server.ts:9:32 - error TS2554: Expected 1 arguments, but got 2.
9 const payment = calculate(100, 0.1);
                                 ~~~
Found 3 errors.
```

**The typescript build fails** with a very verbose message. **The vscode also shows the error** while writing the code on the exact line. This is very convenient and enhances productivity immensely.

So, the correct code in TypeScript:

```
interface Invoice{
    price: number,
    discount: number
};

const calculate = ({ price, discount }: Invoice): number => {
    return price - discount * price;
}

const payment = calculate(<Invoice>{ price: 100, discount: 0.1 });
console.log(payment) // logs 90
```

This is the reason our architecture in the open-source [project](https://github.com/afteracademy/nodejs-backend-architecture-typescript) has adopted TypeScript.

### Separation of Concern

This single most important principle can make your application being developed with confidence as you can be sure to use it without any surprises. It can also be unit tested very easily.

How does separation of concern looks in the given project?

```
├── src
│   ├── database
│   │   ├── model
│   │   │   └── User.ts
│   │   └── repository
│   │       └── UserRepo.ts
│   ├── helpers
│   │   └── validator.ts
│   ├── routes
│   │   └── v1
│   │       └── profile
│   │           ├── schema.ts
│   │           └── user.ts
```

This is a portion of the project structure. The role of each component is clearly defined. The **/src/database/model/User.ts** is the database model that defines the schema for the **MongoDB** `User` document in `users` collection. The structure of the file is listed below:

```
import { model, Schema, Document, Types } from 'mongoose';
import Role from './Role';

export const DOCUMENT_NAME = 'User';
export const COLLECTION_NAME = 'users';

export default interface User extends Document{
    name:string;
    email?:string;
    ...
}

const schema = new Schema(
    {
        name:{
            type:Schema.Types.String,
            required:true,
            trim:true,
            maxlength:100,
        },
        email:{
            type:Schema.Types.String,
            required:true,
            unique:true,
            trim:true,
            select:false
        },
        ...
    });

export const UserModel = model<User>(DOCUMENT_NAME, schema, COLLECTION_NAME);
```

Similarly, we have the `UserRepo`, which has the role of providing all the queries to the other application components related to `User`. `UserRepo` class's methods return the **plain object as the query result and not the Mongoose document.** This data layer is designed to only be concerned with the mode of data storage and the **consumer of the data does not have to be aware of that mode.**

This is also useful in situations which involve the framework migration. For example, when we have to migrate from **MongoDB** to **MySQL** then we just have to **change the Repository** implementation.

The structure of the `UserRepo` class in **/src/database/repository/UserRepo.ts**

```
import User, { UserModel } from '../model/User';
import Role, { RoleModel } from '../model/Role';
import { Types } from 'mongoose';
...

export default class UserRepo{

   // contains critical information of the user
   public static findById(id: Types.ObjectId): Promise<User> {
      return UserModel.findOne({ _id: id, status: true })
         .select('+email +password +roles')
         .populate({
            path: 'roles',
            match: { status: true }
         })
         .lean<User>()
         .exec();
   }
   ...
}
```

The same principle is also applied to the rest of the files and classes.

### Feature Enpasulation

This means that we **group the files related to a single feature together**. This has helped me to **reuse my codebase across projects.** Let's face it we do not write everything again and again but rather copy-paste the code once perfected to all the required places. If all the things are clubbed together then it's super easy to achieve this safely. This also helps in building a logical structure in mind to find a particular file while writing code that needs it as a dependency.

In the project, you can find this same principle applied. Example: **src/routes/v1/profile/schema.ts**

```
import Joi from '@hapi/joi';
import { JoiObjectId } from '../../../helpers/validator';

export default {
   userId: Joi.object().keys({
      id: JoiObjectId().required()
   }),
   profile: Joi.object().keys({
      name: Joi.string().optional().min(1).max(200),
      profilePicUrl: Joi.string().optional().uri(),
   }),
};
```

This file contains the **validations for the API** request. It is placed in the profile feature directory because is it related to profile route handler → **/src/routes/v1/profile/user.ts**

```
import express from 'express';
import { SuccessResponse } from '../../../core/ApiResponse';
import UserRepo from '../../../database/repository/UserRepo';
import { ProtectedRequest } from 'app-request';
import { BadRequestError } from '../../../core/ApiError';
import validator, { ValidationSource } from '../../../helpers/validator';
import schema from './schema';
import asyncHandler from '../../../helpers/asyncHandler';
import _ from 'lodash';
...

const router = express.Router();

router.get('/public/id/:id', validator(schema.userId, ValidationSource.PARAM),
   asyncHandler(async (req: ProtectedRequest, res, next) => {
      const user = await UserRepo.findPublicProfileById(new Types.ObjectId(req.params.id));
      if (!user) throw new BadRequestError('User not registered');
      return new SuccessResponse('success', _.pick(user, ['name', 'profilePicUrl'])).send(res);
   }));
...

export default router;
```

### Better Error Handling

This is very important for the application to be consistent with errors and the corresponding API responses. So, adopting the separation of concern principle and also the uniformity in the API responses, I have created `ApiError` class [**/src/core/ApiError.ts**]. This class defines all the possible error classes and their appropriate handling. The other application components can use this class to send the error responses to the client by simply **passing the error instances in the next function**.

In the above code you can observe the fetch profile by id API simply throws the error [**`new** BadRequestError(**'**User not registered**'**)`] and that error is handled in the `ApiError → handle` function. This makes it very convenient in writing the logic for any API route handler.

```
export class BadRequestError extends ApiError{
   constructor(message: string = 'Bad Request') {
      super(ErrorType.BAD_REQUEST, message);
   }
}
```

The base class: `ApiError`

```
export abstract class ApiError extends Error{

   constructor(public type: ErrorType, public message: string = 'error') {
      super(type);
   }

   public static handle(err: ApiError, res: Response): Response {
      switch (err.type) {
         case ErrorType.BAD_REQUEST:
            return new BadRequestResponse(err.message).send(res);
         ...
      }
   }
}
```

### Better Response Handling

The same reason as provided in the above error handling example is also valid for the response handling. So, I have created the class **ApiResponses.ts** located at **/src/core/ApiResponses.ts**.

To send a response as shown in the above profile fetch API, we simply need to call `new SuccessResponse('MESSAGE', RESPONSE_OBJECT).send(res);`. All the other aspects of it, for example, maintaining a uniform response structure, adding the cache-control, setting the response HTTP status, removing the undefined keys, etc are handled by the `ApiResponse` class itself.

```
export class SuccessResponse<T> extends ApiResponse{

   constructor(message: string, private data: T) {
      super(StatusCode.SUCCESS, ResponseStatus.SUCCESS, message);
   }

   send(res: Response): Response {
      return super.prepare<SuccessResponse<T>>(res, this);
   }
}
```

The base class: `ApiResponses`

```
abstract class ApiResponse{

   constructor(protected statusCode: StatusCode, protected status: ResponseStatus, protected message: string) { }

   protected prepare<T extends ApiResponse>(res: Response, response: T): Response {
      return res.status(this.status).json(ApiResponse.sanitize(response));
   }

   public send(res: Response): Response {
      return this.prepare<ApiResponse>(res, this);
   }

   private static sanitize<T extends ApiResponse>(response: T): T {
      const clone: T = <T>{};
      Object.assign(clone, response);
      // delete {some_field};
      delete clone.status;
      for (const i in clone) if (typeof clone[i] === 'undefined') delete clone[i];
      return clone;
   }
}
```

### Better Promise Management

The callback is replaced by Promises and now the Promise chain is replaced by the async/await. This greatly enhances the coding experience. One problem with this implementation is to write the **ugly try/catch block**. In order to give it sugar, I have created a middleware function `asyncHandler`.

> All the utility middleware functions are placed in the /src/helpers
> 

```
import { Request, Response, NextFunction } from 'express';

type AsyncFunction = (req: Request, res: Response, next: NextFunction) => Promise<any>;

export default (execution: AsyncFunction)=> (req: Request, res: Response, next: NextFunction) => {
   execution(req, res, next).catch(next);
};
```

It is used as a wrapper for the other route handler's middleware functions.

```
router.get('/some-route',
   asyncHandler(async (req: ProtectedRequest, res, next) => {
      // No need for try/catch block
      // Simple throw Error instance and it will be handled
   }));
```

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/android-course-subscription-banner.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/android-course-subscription-banner.png)

### Robust Unit Tests

I can not emphasize more on writing tests. It's a non-optional exercise. So, we need to mock a lot of classes if we need to unit test. I have used **Jest** framework for it. The **tests** have the same directory structure as the **src** so that the tests can be mapped with ease.

Test structure example from the project:

```
├── tests
│   ├── auth
│   │   └── apikey
│   │       ├── mock.ts
│   │       └── unit.test.ts
│   ├── core
│   │   └── jwt
│   │       ├── mock.ts
│   │       └── unit.test.ts
│   ├── routes
│   │   └── v1
│   │       └── login
│   │           ├── integration.test.ts
│   │           ├── mock.ts
│   │           └── unit.test.ts
│   ├── .env.test
│   └── setup.ts
```

Example of the JWT unit test:

**tests/core/jwt/mock.ts**

```
import fs from 'fs';

export const readFileSpy = jest.spyOn(fs, 'readFile');
```

**tests/core/jwt/unit.test.ts**

```
import { readFileSpy } from './mock';
import JWT, { JwtPayload, ValidationParams } from '../../../src/core/JWT';
import { BadTokenError, TokenExpiredError } from '../../../src/core/ApiError';

describe('JWT class tests', () => {

   const issuer = 'issuer';
   const audience = 'audience';
   const subject = 'subject';
   const param = 'param';
   const validity = 1;

   it('Should throw error for invalid token in JWT.decode', async () => {

      beforeEach(() => {
         readFileSpy.mockClear();
      });

      try {
         await JWT.decode('abc');
      } catch (e) {
         expect(e).toBeInstanceOf(BadTokenError);
      }

      expect(readFileSpy).toBeCalledTimes(1);
   });
   ...
});
```

> Similary, I have added integration tests. You can find the example of this at tests/routes/v1/login/integration.test.ts
> 

### Simple Deployability

I have added the **Dockerfile** and **docker-compose.yml** to simplify the deployment of the application. It is also possible to manually deploy the application. The instruction for it can be found in the [repository](https://github.com/afteracademy/nodejs-backend-architecture-typescript) itself.

Let me give you an overview of the instructions written in the **Dockerfile** and **docker-compose.yml**:

1. On the local machine docker, download and install the node image.
2. For Node, application creates a directory on the host and copy the src code to the host.
3. Install the application dependencies, build the typescript, and start the server.
4. Download and install the MongoDB image
5. Create the root user, and then run the seeding script defined at **/addons/init-mongo.js**.
6. The seeding script creates the database and a user of that database. It also adds the prerequisite documents for **roles** and **api_keys** in the collections of that database.

**Now you know why this architecture has a certain structure and the role of various components in that architecture.**

### **3RE Architecture**

Now, let's understand how the request and response are processed in the given project architecture. I have called this architecture **3RE Architecture**, a short name for Router, RouteHandler, ResponseHandler, and ErrorHandler.

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/3re-2deb24029010e830.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/3re-2deb24029010e830.png)

**The request processing flow in these terms**: Signup request handling example:

`/src → server.ts → app.ts → /routes/v1/index.ts → /auth/apikey.ts → schema.ts → /helpers/validator.ts → asyncHandler.ts → /routes/v1/signup.ts → schema.ts → /helpers/validator.ts → asyncHandler.ts → /database/repository/UserRepo.ts → /database/model/User.ts → /core/ApiResponses.ts`

1. The request is routed to its corresponsding handler via Router **/src/routes/v1/index.ts**
2. The RouteHandler is called for that particular endpoint (**Example: /src/routes/v1/access/signup.ts**)
3. Based on the validations and request it is either sent to the ErrorHandler [`app.use((err: Error, req: Request, res: Response, next: NextFunction) => {**ApiError.handle(err)**;})`].
4. Else it is handled by the ResponseHandler i.e. **ApiResponse → send(res)**

### Blogging Platform Building

The complete API has been built to create a Blogging platform. We at AfterAcademy are using a similar version of the web services for this very blog that you are reading now. You can find the complete API reference doc developed in this project on this **[link: API Documentation](https://documenter.getpostman.com/view/1552895/SzYUZg52?version=latest)**

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/project-outline-66fa906beed2e2c9.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/project-outline-66fa906beed2e2c9.png)

### Security Implementation

Security has been considered as the most important thing while building this project.

1. The configuration is loaded though environment variables [**.env** file].
2. JWT based **authentication** in adopted.
3. Role-based **Authorization** has been developed.

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/api-structure-64a517fa6d112a88.png](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/api-structure-64a517fa6d112a88.png)

> That's it for this blog. I hope you must have enjoyed reading it as much as I enjoyed writing it.
> 

### **The video guide to build and run the project**

Let me know your feedback in the comments below and also mention other topics you would want me to write.

**Please, share this blog so that others can learn from it.**

**Take Care and Keep Learning**

![Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/banner-mindorks-google-interview-598e36e04a9b0a37.jpg](Design%20Node%20js%20Backend%20Architecture%20like%20a%20Pro%20d206b068a7784162a1d51e6e6eea7f2d/banner-mindorks-google-interview-598e36e04a9b0a37.jpg)