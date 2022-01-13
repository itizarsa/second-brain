# Starting a TypeScript Project in 2021 · Chris Hager

Source: Article
Status: Unprocessed
URL: https://www.metachris.com/2021/04/starting-a-typescript-project-in-2021/

![https://www.metachris.com/images/posts/typescript-2021.jpg](https://www.metachris.com/images/posts/typescript-2021.jpg)

---

![typescript-2021.jpg](Starting%20a%20TypeScript%20Project%20in%202021%20%C2%B7%20Chris%20Hage%20b9222ddbe2fc4fbc9b1fc4c0fa5e5dfb/typescript-2021.jpg)

You can use the [example repository](https://github.com/metachris/typescript-boilerplate) (instead of the manual setup in this guide):

```
git clone https://github.com/metachris/typescript-boilerplate.git

```

```
# Create project folder
mkdir my-project
cd my-project

# Create source folder and files
mkdir src
touch src/main.ts src/main.test.ts src/cli.ts

# Create a package.json
yarn init

# Install TypeScript, linter and Jest
yarn add -D typescript @types/node ts-node
yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
yarn add -D jest ts-jest @types/jest

# Get a .gitignore
wget https://raw.githubusercontent.com/metachris/typescript-boilerplate/master/.gitignore

# Get a tsconfig.json with some defaults (adapt as needed)
wget https://raw.githubusercontent.com/metachris/typescript-boilerplate/master/tsconfig.json

# Alternatively you can create a fresh tsconfig.json (with extensive docstrings)
tsc --init

# Get a .eslintrc.js
wget https://raw.githubusercontent.com/metachris/typescript-boilerplate/master/.eslintrc.js

# Get a jest.config.json, for ts-jest to run the tests without a separate typescript compile step
wget https://raw.githubusercontent.com/metachris/typescript-boilerplate/master/jest.config.js

# Create a git repo and make the first commit
git init
git add .
git commit -am "initial commit"

```

Use `src/cli.ts` for code that’s run from the command line. This way code from `main.ts` can be included without running the entrypoint code, and allows for easier cross-target building and code branches (eg. Node.js and browsers).

```
{
    "scripts": {
        "cli": "ts-node src/cli.ts",
        "test": "jest",
        "lint": "eslint src/ --ext .js,.jsx,.ts,.tsx",
        "build": "tsc -p tsconfig.json",
        "clean": "rm -rf dist build",
        "ts-node": "ts-node"
    }
}

```

💡 In Visual Studio Code you can use the build and test tasks to start scripts with keyboard shortcuts. In the command palette “*Configure Default Build Task*” and “*Configure Default Test Task*” (see the [VS Code docs](https://code.visualstudio.com/docs/editor/tasks)).

```
import { greet } from './main'

test('the data is peanut butter', () => {
  expect(1).toBe(1)
});

test('greeting', () => {
  expect(greet('Foo')).toBe('Hello Foo')
});

```

```
yarn add -D esbuild

```

```
# Compile and bundle
yarn esbuild src/cli.ts --bundle --platform=node --outfile=dist/esbuild/cli.js

# Same, but minify and sourcemaps
yarn esbuild src/cli.ts --bundle --platform=node --minify --sourcemap=external --outfile=dist/esbuild/cli.js

# Run the bundled output
node dist/esbuild/cli.js

```

```
# Bundle for browsers
yarn esbuild src/browser.ts --bundle --outfile=dist/esbuild/browser.js

# Same, but with minification and sourcemaps
yarn esbuild src/browser.ts --bundle --minify --sourcemap=external --outfile=dist/esbuild/browser.js

```

esbuild has a `--global-name=xyz` flag, to store the exports from the entry point in a global variable. See also the [esbuild “Global name” docs](https://esbuild.github.io/api/#global-name).

```
"lib": ["ES6", "DOM"]

```

```
// Import a function
import { greet } from './main'

// Make it accessible on the window object
(window as any).greet = greet

```

```
yarn esbuild src/browser.ts --bundle --outfile=dist/esbuild/browser.js

```

- The example repository includes the `esbuild` commands as [scripts in package.json](https://github.com/metachris/typescript-boilerplate/blob/master/package.json)
- If you prefer to use [webpack](https://webpack.js.org/), take a look at this [webpack.config.js](https://github.com/metachris/micropython-ctl/blob/master/webpack.config.js) for inspiration
- Rather than casting `window` to `any`, you might want to properly extend the `Window` interface ([see here](https://stackoverflow.com/a/43513740/5433572))

npm and yarn ignore the files from `.gitignore`. Since `dist` is in there, we need to overwrite the npm ignore settings using a custom `.npmignore`:

```
wget https://raw.githubusercontent.com/metachris/micropython-ctl/master/.npmignore

```

```
# Build with tsc and esbuild
yarn build-all

# Update the version and publish to npm
yarn publish

```

```
npm install typescript-boilerplate-2021

# or with yarn
yarn add typescript-boilerplate-2021

```

```
import { greet } from 'typescript-boilerplate-2021'

greet("World")

```

```
<script src="https://cdn.jsdelivr.net/npm/typescript-boilerplate-2021@0.3.0"></script>

```

```
name: Lint and test

on: [push, pull_request]

jobs:
  lint_and_test:
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        nodejs: [10, 12, 14]

    steps:
    - uses: actions/checkout@v2

    # https://github.com/actions/setup-node
    - uses: actions/setup-node@v2-beta
      with:
        node-version: ${{ matrix.nodejs }}

    - run: yarn install
    - run: yarn test
    - run: yarn lint
    - run: yarn build-all

```

```
jobs:
  default-version:
    runs-on: ${{ matrix.os }}
    strategy:
      fail-fast: false
      matrix:
        os: [macos-latest, windows-latest, ubuntu-latest]

    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v2-beta
      with:
        node-version: 12
    ...

```

```
image: node:12

cache:
  paths:
    - node_modules/

stages:
  - test

lint-and-test:
  stage: test
  script:
    - yarn install
    - yarn test
    - yarn lint
    - yarn build-all

```

```
/**
 * This comment _supports_ [Markdown](https://marked.js.org/)
 */
export class DocumentMe {}

```

You can use the [boilerplate repository](https://github.com/metachris/typescript-boilerplate) like this:

```
git clone https://github.com/metachris/typescript-boilerplate.git
cd typescript-boilerplate

yarn install
yarn test
yarn lint
yarn build-all

```