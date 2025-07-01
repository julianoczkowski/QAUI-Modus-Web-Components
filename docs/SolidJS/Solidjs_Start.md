TITLE: Create and Run a SolidStart Application
DESCRIPTION: Instructions to initialize a new SolidStart project and start its development server using common package managers like npm, pnpm, or Bun.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
mkdir my-app
cd my-app

# with npm
npm init solid@latest
npm install
npm run dev

# or with pnpm
pnpm create solid@latest
pnpm install
pnpm dev

# or with Bun
bun create solid@latest
bun install
bun dev
```

---

TITLE: SolidStart Project Initialization and Development Setup
DESCRIPTION: These commands provide the quickest way to initialize a new SolidStart project, navigate into its directory, install necessary dependencies, and start the local development server. This sequence is essential for setting up a functional SolidStart application from scratch.
SOURCE: https://github.com/solidjs/solid-start/blob/main/packages/start/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest my-app
cd my-app
npm install
npm run dev
```

---

TITLE: Create SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project, either in the current directory or a specified new directory. This requires `npm` to be installed.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/hackernews/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project
DESCRIPTION: Commands to create a new SolidStart project. You can either create it in the current directory or specify a new directory name for the project.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/bare/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project with npm
DESCRIPTION: This snippet demonstrates how to create a new SolidStart project using `npm init solid@latest`. It provides commands for initializing a project in the current directory or a specified new directory, `my-app`.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-tailwindcss/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project
DESCRIPTION: Use `npm init solid@latest` to create a new SolidStart project. This command can either initialize a project in the current directory or create a new directory for the project.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-drizzle/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project. Users can choose to create the project in the current directory or specify a new directory name for the project.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/todomvc/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Initialize New SolidStart Project
DESCRIPTION: Use `npm init solid@latest` to create a new SolidStart project. You can specify a directory name to create the project in a new folder, or omit it to initialize in the current directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-solidbase/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project
DESCRIPTION: This snippet demonstrates how to initialize a new SolidStart project using `npm init solid@latest`. It shows commands for creating a project in the current directory or a specified new directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-vitest/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project using npm. You can create a project in the current directory or specify a new directory name.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-prisma/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project using `npm init solid@latest`, allowing creation in the current directory or a specified new directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-mdx/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project
DESCRIPTION: Commands to create a new SolidStart project. You can either initialize it in the current directory or specify a new directory name for the project.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-auth/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Initialize SolidStart Project
DESCRIPTION: Use `npm init solid@latest` to create a new SolidStart project. This command allows creating a project in the current directory or a specified new directory, setting up the basic project structure and dependencies.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-unocss/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Clone Solid-Start Repository
DESCRIPTION: Clones the Solid-Start project repository from GitHub to your local machine, initiating the development environment setup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/CONTRIBUTING.md#_snippet_0

LANGUAGE: Shell
CODE:

```
git clone https://github.com/solidjs/solid-start.git
```

---

TITLE: Run a Solid-Start Example Application
DESCRIPTION: Starts the development server for a specific example application, such as 'example-hackernews', allowing local testing and verification of changes.
SOURCE: https://github.com/solidjs/solid-start/blob/main/CONTRIBUTING.md#_snippet_3

LANGUAGE: Shell
CODE:

```
pnpm --filter example-hackernews run dev
```

---

TITLE: Setup and Run Integration Tests
DESCRIPTION: Provides commands for setting up Playwright, running all integration tests, and viewing the detailed test report to ensure code quality and functionality.
SOURCE: https://github.com/solidjs/solid-start/blob/main/CONTRIBUTING.md#_snippet_4

LANGUAGE: Shell
CODE:

```
pnpm run install:playwright
```

LANGUAGE: Shell
CODE:

```
pnpm run test:all
```

LANGUAGE: Shell
CODE:

```
pnpm run show:test-report
```

---

TITLE: Build All Project Dependencies
DESCRIPTION: Executes the 'build:all' script to compile and build all internal dependencies of the Solid-Start project, preparing them for use.
SOURCE: https://github.com/solidjs/solid-start/blob/main/CONTRIBUTING.md#_snippet_2

LANGUAGE: Shell
CODE:

```
pnpm run build:all
```

---

TITLE: Install Project Dependencies
DESCRIPTION: Installs all necessary project dependencies using pnpm, ensuring all required packages are available for development and building.
SOURCE: https://github.com/solidjs/solid-start/blob/main/CONTRIBUTING.md#_snippet_1

LANGUAGE: Shell
CODE:

```
pnpm install
```

---

TITLE: Install pnpm Globally
DESCRIPTION: Command to install the pnpm package manager globally using npm, which is recommended for managing dependencies in the SolidStart monorepo.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm install -g pnpm
```

---

TITLE: Run SolidStart Project Tests
DESCRIPTION: This snippet shows the command to execute tests for a SolidStart project. Tests are configured to run with `vitest`, `@solidjs/testing-library`, and `@testing-library/jest-dom`.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-vitest/README.md#_snippet_2

LANGUAGE: sh
CODE:

```
npm test
```

---

TITLE: Build SolidStart Application for Production
DESCRIPTION: The `npm run build` command compiles a SolidStart project for deployment. By default, it generates a Node.js application. Users can configure different deployment presets in `app.config.js` and `package.json` to optimize for various environments.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-unocss/README.md#_snippet_2

LANGUAGE: bash
CODE:

```
npm run build
```

---

TITLE: Build SolidStart Application for Deployment
DESCRIPTION: Build your SolidStart application for deployment using `npm run build`. Solid apps use adapters to optimize for different environments, generating a Node app by default. Custom adapters can be specified in `app.config.js`.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-drizzle/README.md#_snippet_2

LANGUAGE: bash
CODE:

```
npm run build
```

---

TITLE: Build and Run SolidStart Application
DESCRIPTION: Commands to build the SolidStart application for production deployment and then run the compiled Node.js application. SolidStart uses presets to optimize builds for different environments.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-prisma/README.md#_snippet_2

LANGUAGE: bash
CODE:

```
npm run build
npm start
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to launch the development server for a SolidStart project. An option is available to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-auth/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Run SolidStart Development Server
DESCRIPTION: After installing dependencies, use `npm run dev` to start the local development server. The command can be run to simply start the server or to automatically open the application in a new browser tab.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-drizzle/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

npm run dev
```

---

TITLE: Run SolidStart Development Server
DESCRIPTION: After installing dependencies, use `npm run dev` to start the local development server for a SolidStart application. An additional flag `--open` can be used to automatically launch the application in a web browser.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-unocss/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: This snippet shows how to start the development server for a SolidStart project after dependencies have been installed. It includes the standard command `npm run dev` and an option to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-trpc/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to launch the development server for a SolidStart project. Includes an option to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-prisma/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to launch the development server for a SolidStart project. An option is available to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/bare/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project after dependencies have been installed. The first command starts the server, while the second includes an option to automatically open the application in a new browser tab upon startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/archived_test/template/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project after dependencies are installed. An option is available to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-solid-styled/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: This snippet provides commands to start the development server for a SolidStart project. It includes options to simply run the server or to automatically open the application in a new browser tab upon startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-vitest/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project. After installing dependencies, use these commands to run your application locally. An option is provided to automatically open the app in a new browser tab.
SOURCE: https://github.com/solidjs/solid-start/blob/main/archived_examples/notes/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to launch the development server for a SolidStart project. An optional flag allows the application to automatically open in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/todomvc/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to launch the development server for a SolidStart project, including an option to automatically open the application in a new browser tab upon startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-tanstack-router/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project using `npm run dev`, with an option to automatically open the application in a new browser tab.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-mdx/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Run the development server for a SolidStart project after installing dependencies. Options include starting the server normally or opening the application in a new browser tab automatically.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/experiments/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project after dependencies are installed. An option is available to automatically open the application in a new browser tab upon server startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/packages/tests/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: After installing dependencies, run `npm run dev` to start the development server. Add `-- --open` to automatically open the application in your default web browser.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-solidbase/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Build SolidStart Project with pnpm
DESCRIPTION: Command to build the SolidStart project within a monorepo using pnpm.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_3

LANGUAGE: bash
CODE:

```
pnpm build
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project. Includes an option to automatically open the application in a new browser tab.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/basic/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: After creating a project and installing dependencies, use these commands to start the development server. The '--open' flag automatically launches the application in a new browser tab, streamlining the development workflow.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/notes/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project using `npm init solid@latest`. Users can create a project in the current directory or a specified new directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/basic/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: These commands initialize a new SolidStart project. You can either create it in the current directory or specify a new directory name for the project. This requires Node.js and npm to be installed.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/notes/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Install Dependencies and Run SolidStart Application
DESCRIPTION: These commands provide instructions for setting up and running the SolidStart application. First, install all necessary project dependencies using npm or yarn. Then, start the development server which includes hot reload functionality, accessible at localhost:3000.
SOURCE: https://github.com/solidjs/solid-start/blob/main/archived_examples/movies/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
$ npm install # Or yarn install

# serve with hot reload at localhost:3000
$ npm run dev
```

---

TITLE: Importing and Using a SolidJS Component
DESCRIPTION: This snippet illustrates the standard way to import a custom component from a local path and render it within a SolidJS application's JSX/TSX structure.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-mdx/src/routes/index.mdx#_snippet_0

LANGUAGE: TypeScript
CODE:

```
import Counter from "~/components/Counter";

<Counter />
```

---

TITLE: Importing Components in SolidJS
DESCRIPTION: Demonstrates how to import a component named 'Counter' from a local path using SolidJS's module resolution, typically configured to resolve paths starting with `~`.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-mdx/src/routes/about.mdx#_snippet_0

LANGUAGE: JavaScript
CODE:

```
import Counter from "~/components/Counter";
```

---

TITLE: Set HTTP 404 Status Code in SolidStart
DESCRIPTION: This snippet shows how to use the `HttpStatusCode` component from `@solidjs/start` to explicitly set the HTTP status code of a page to 404 (Not Found). This is typically used for pages that handle routes not matching any defined path, ensuring proper server response for missing resources.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-solidbase/src/routes/[...404].mdx#_snippet_0

LANGUAGE: TypeScript
CODE:

```
import { HttpStatusCode } from "@solidjs/start";

<HttpStatusCode code={404} />
```

---

TITLE: Set HTTP 404 Not Found Status in SolidJS
DESCRIPTION: This snippet illustrates the complete process of setting an HTTP 404 (Not Found) status code for a page in a SolidJS application. It includes importing the necessary component and its usage within a JSX context to signal to the client that the requested resource was not found.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-mdx/src/routes/[...404].mdx#_snippet_0

LANGUAGE: JavaScript
CODE:

```
import { HttpStatusCode } from "@solidjs/start";
```

LANGUAGE: JSX
CODE:

```
<HttpStatusCode code={404} />
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: After installing dependencies, this snippet shows how to launch the development server for a SolidStart project. It includes options to simply start the server or to automatically open the application in a new browser tab upon startup.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-tailwindcss/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

npm run dev -- --open
```

---

TITLE: Start SolidStart Development Server
DESCRIPTION: Commands to start the development server for a SolidStart project after dependencies have been installed. Includes an option to automatically open the application in a new browser tab.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/hackernews/README.md#_snippet_1

LANGUAGE: bash
CODE:

```
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

---

TITLE: Install Monorepo Dependencies with pnpm
DESCRIPTION: Command to install all dependencies for SolidStart packages and examples within a monorepo using pnpm.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_2

LANGUAGE: bash
CODE:

```
pnpm install
```

---

TITLE: Create a New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project. You can create a project in the current directory or specify a new directory name.
SOURCE: https://github.com/solidjs/solid-start/blob/main/archived_examples/notes/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid

# create a new project in my-app
npm init solid my-app
```

---

TITLE: Yarn Workspaces nohoist Configuration (Workspace Root)
DESCRIPTION: JSON configuration for Yarn workspaces to prevent hoisting of the `@solidjs/start` dependency from the workspace root, ensuring correct script loading within individual packages.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_4

LANGUAGE: json
CODE:

```
{
  "workspaces": {
    "packages": [
      /* ... */
    ],
    "nohoist": ["**/@solidjs/start"]
  }
}
```

---

TITLE: Yarn v2+ installConfig for Dependency Hoisting
DESCRIPTION: JSON configuration for Yarn v2 or higher to manage dependency hoisting limits within a project, specifically preventing `@solidjs/start` from being hoisted by setting `hoistingLimits`.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_6

LANGUAGE: json
CODE:

```
{
  "installConfig": {
    "hoistingLimits": "dependencies"
  }
}
```

---

TITLE: Yarn Workspaces nohoist Configuration (Project Root)
DESCRIPTION: JSON configuration for Yarn workspaces to prevent hoisting of the `@solidjs/start` dependency from a specific child package's root, ensuring correct script loading.
SOURCE: https://github.com/solidjs/solid-start/blob/main/README.md#_snippet_5

LANGUAGE: json
CODE:

```
{
  "workspaces": {
    "nohoist": ["@solidjs/start"]
  }
}
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project, either in the current directory or a specified new directory. This uses the `npm init` command with the `@latest` tag to ensure the most recent version of SolidStart is used.
SOURCE: https://github.com/solidjs/solid-start/blob/main/archived_test/template/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project. You can create a project in the current directory or specify a new directory name for the project.
SOURCE: https://github.com/solidjs/solid-start/blob/main/packages/tests/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Create a New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project using npm, allowing creation in the current directory or a specified new directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-tanstack-router/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm init solid@latest

npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: This snippet provides commands to initialize a new SolidStart project using `npm init solid@latest`. It demonstrates how to create a project in the current directory or within a specified new directory, setting up the basic project structure.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-trpc/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Create New SolidStart Project
DESCRIPTION: Commands to initialize a new SolidStart project. You can create a project in the current directory or specify a new directory name.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/with-solid-styled/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```

---

TITLE: Create a New SolidStart Project
DESCRIPTION: Initialize a new Solid.js project using `npm init solid@latest`. This command can create a project in the current directory or a specified new directory.
SOURCE: https://github.com/solidjs/solid-start/blob/main/examples/experiments/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
# create a new project in the current directory
npm init solid@latest

# create a new project in my-app
npm init solid@latest my-app
```
