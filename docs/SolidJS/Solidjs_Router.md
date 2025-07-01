TITLE: SolidJS Router: Implementing Preload for Data Fetching
DESCRIPTION: This snippet demonstrates how to implement the new preload mechanism in SolidJS Router, replacing the older `data` functions. It shows how to define a `preload` function that fetches data using `createResource` and pass it to a `Route` definition, disabling the default router preload.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_56

LANGUAGE: js
CODE:

```
import { lazy } from "solid-js";
import { Route } from "@solidjs/router";

const User = lazy(() => import("./pages/users/[id].js"));

// preload function
function preloadUser({params, location}) {
  const [user] = createResource(() => params.id, fetchUser);
  return user;
}

// Pass it in the route definition
<Router preload={false}>
  <Route path="/users/:id" component={User} preload={preloadUser} />
</Router>
```

---

TITLE: Install Solid Router Package
DESCRIPTION: Installs the Solid Router package using npm, which is the first step to integrate the router into your SolidJS application.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_0

LANGUAGE: sh
CODE:

```
npm i @solidjs/router
```

---

TITLE: Netlify: Configuring Redirects for Single Page Applications
DESCRIPTION: This snippet provides the configuration for Netlify to correctly handle client-side routing in Single Page Applications (SPAs). It shows how to create a `_redirects` file that redirects all paths to `index.html` with a 200 status code, preventing 404 errors for non-existent server paths.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_58

LANGUAGE: sh
CODE:

```
/*   /index.html   200
```

---

TITLE: Vercel: Configuring Rewrites for Single Page Applications
DESCRIPTION: This snippet provides the configuration for Vercel to correctly handle client-side routing in Single Page Applications (SPAs). It shows how to add a `rewrites` section to `vercel.json` that redirects all incoming requests to `index.html`, ensuring the client-side router takes over.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_59

LANGUAGE: json
CODE:

```
{
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

---

TITLE: Initialize Solid Router in Application
DESCRIPTION: Renders the Solid Router component as the root of your application, setting up the core mechanism for URL matching and page display. This is essential for the router to function.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_1

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import { Router } from "@solidjs/router";

render(
  () => <Router />,
  document.getElementById("app")
);
```

---

TITLE: Configure Solid Router with Array of Route Definitions
DESCRIPTION: Demonstrates how to set up routes in SolidJS by passing an array of RouteDefinition objects to the <Router> component. This allows for nested routes and lazy loading of components.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_35

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router } from "@solidjs/router";

const routes = [
  {
    path: "/users",
    component: lazy(() => import("/pages/users.js")),
  },
  {
    path: "/users/:id",
    component: lazy(() => import("/pages/users/[id].js")),
    children: [
      {
        path: "/",
        component: lazy(() => import("/pages/users/[id]/index.js")),
      },
      {
        path: "/settings",
        component: lazy(() => import("/pages/users/[id]/settings.js")),
      },
      {
        path: "/*all",
        component: lazy(() => import("/pages/users/[id]/[...all].js")),
      },
    ],
  },
  {
    path: "/",
    component: lazy(() => import("/pages/index.js")),
  },
  {
    path: "/*all",
    component: lazy(() => import("/pages/[...all].js")),
  },
];

render(() =>
  <Router>{routes}</Router>,
  document.getElementById("app")
);
```

---

TITLE: Manage Query Parameters with useSearchParams (SolidJS Router)
DESCRIPTION: Retrieves a tuple for reading and updating the current location's query parameters. The first element is a reactive proxy object for accessing parameters, and the second is a setter method. The setter merges new entries, removes keys for empty values, and behaves like a navigation, disabling auto-scrolling by default.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_47

LANGUAGE: js
CODE:

```
const [searchParams, setSearchParams] = useSearchParams();

return (
  <div>
    <span>Page: {searchParams.page}</span>
    <button
      onClick={() =>
        setSearchParams({ page: (parseInt(searchParams.page) || 0) + 1 })
      }
    >
      Next Page
    </button>
  </div>
);
```

---

TITLE: SolidJS: Accessing Preloaded Data in Components via Context
DESCRIPTION: This snippet illustrates how to access data preloaded by the SolidJS Router within a component. It shows how to wrap component content with a `UserContext.Provider` to make the preloaded `props.data` available, and then consume it using `useContext` in child components.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_57

LANGUAGE: js
CODE:

```
function User(props) {
  <UserContext.Provider value={props.data}>
    {/* my component content  */}
  </UserContext.Provider>
}

// Somewhere else
function UserDetails() {
  const user = useContext(UserContext)
  // render stuff
}
```

---

TITLE: Consume SolidJS `query` data in a component with `createAsync`
DESCRIPTION: Illustrates how to use the `getUser` query function within a SolidJS page component. It leverages `createAsync` to manage the asynchronous data fetching and display the user's name once the data is available.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_22

LANGUAGE: jsx
CODE:

```
// pages/users/[id].js
import { getUser } from ... // the query function

export default function User(props) {
  const user = createAsync(() => getUser(props.params.id));
  return <h1>{user().name}</h1>;
}
```

---

TITLE: Create Navigation Links to Routes in Solid Router
DESCRIPTION: Use an anchor tag that takes you to a route.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_6

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

const Users = lazy(() => import("./pages/Users"));
const Home = lazy(() => import("./pages/Home"));

const App = props => (
  <>
    <nav>
      <a href="/about">About</a>
      <a href="/">Home</a>
    </nav>
    <h1>My Site with lots of pages</h1>
    {props.children}
  </>
);

render(() => (
  <Router root={App}>
    <Route path="/users" component={Users} />
    <Route path="/" component={Home} />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Configure Solid Router with Basic Routes
DESCRIPTION: Add each route to a <Router> using the Route component, specifying a path and a component to render when the user navigates to that path.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_2

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

import Home from "./pages/Home";
import Users from "./pages/Users";

render(() => (
  <Router>
    <Route path="/users" component={Users} />
    <Route path="/" component={Home} />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Define Basic Dynamic Routes with SolidJS Router
DESCRIPTION: Demonstrates how to set up basic dynamic routes using a colon prefix for parameters (e.g., `:id`). The `User` component will be rendered for paths matching the pattern, and the `id` can be accessed via `useParams`.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_7

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

const Users = lazy(() => import("./pages/Users"));
const User = lazy(() => import("./pages/User"));
const Home = lazy(() => import("./pages/Home"));

render(() => (
  <Router>
    <Route path="/users" component={Users} />
    <Route path="/users/:id" component={User} />
    <Route path="/" component={Home} />
 ), document.getElementById("app"));
```

---

TITLE: Use SolidJS `query` with route `preload`
DESCRIPTION: Shows how to integrate a `query` function with SolidJS Router's `preload` mechanism. The `preloadUser` function is called during route preloading to fetch data proactively, improving user experience.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_21

LANGUAGE: js
CODE:

```
import { lazy } from "solid-js";
import { Route } from "@solidjs/router";
import { getUser } from ... // the query function

const User = lazy(() => import("./pages/users/[id].js"));

// preload function
function preloadUser({params, location}) {
  void getUser(params.id)
}

// Pass it in the route definition
<Route path="/users/:id" component={User} preload={preloadUser} />;
```

---

TITLE: Solid Router: `useParams` Hook for Route Parameters
DESCRIPTION: The `useParams` hook in Solid Router provides a reactive, store-like object containing the current route path parameters. This allows components to dynamically fetch or display data based on values extracted from the URL.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_44

LANGUAGE: js
CODE:

```
const params = useParams();

// fetch user based on the id path parameter
const [user] = createResource(() => params.id, fetchUser);
```

---

TITLE: Solid Router: `useNavigate` Hook for Programmatic Navigation
DESCRIPTION: The `useNavigate` hook retrieves a method for programmatic navigation within Solid Router. It accepts a target path and an optional object to configure navigation behavior, such as resolving paths, replacing history entries, controlling scroll, and passing custom state.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_45

LANGUAGE: APIDOC
CODE:

```
useNavigate Hook Options:
  resolve: boolean
    Default: true
    Description: resolve the path against the current route
  replace: boolean
    Default: false
    Description: replace the history entry
  scroll: boolean
    Default: true
    Description: scroll to top after navigation
  state: any
    Default: undefined
    Description: pass custom state to `location.state`
  Note: The state is serialized using the structured clone algorithm which does not support all object types.
```

LANGUAGE: js
CODE:

```
const navigate = useNavigate();

if (unauthorized) {
  navigate("/login", { replace: true });
}
```

---

TITLE: Define a SolidJS `query` for data fetching
DESCRIPTION: Demonstrates how to define a `query` function using the `query` API. It takes an async function and a query key, enabling deduping, caching, and revalidation. Arguments to the query function are expected to be serializable.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_20

LANGUAGE: jsx
CODE:

```
const getUser = query(async (id) => {
  return (await fetch(`/api/users${id}`)).json()
}, "users") // used as the query key + serialized arguments
```

---

TITLE: Using props.children with Nested Route Components in SolidJS
DESCRIPTION: Shows how to leverage `props.children` within a parent route component (`PageWrapper`) to render nested route elements inside a common layout, maintaining the route configuration while providing a shared wrapper.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_15

LANGUAGE: jsx
CODE:

```
function PageWrapper(props) {
  return (
    <div>
      <h1> We love our users! </h1>
      {props.children}
      <A href="/">Back Home</A>
    </div>
  );
}

<Route path="/users" component={PageWrapper}>
  <Route path="/" component={Users} />
  <Route path="/:id" component={User} />
</Route>;
```

---

TITLE: Create a CatchAll Route (404 Page) in Solid Router
DESCRIPTION: We can create catchall routes for pages not found at any nested level of the router. We use `*` and optionally the name of a parameter to retrieve the rest of the path.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_4

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

import Home from "./pages/Home";
import Users from "./pages/Users";
import NotFound from "./pages/404";

const App = props => (
  <>
    <h1>My Site with lots of pages</h1>
    {props.children}
  </>
)

render(() => (
  <Router root={App}>
    <Route path="/users" component={Users} />
    <Route path="/" component={Home} />
    <Route path="*404" component={NotFound} />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Provide a Root Level Layout in Solid Router
DESCRIPTION: This will always be there and won't update on page change. It is the ideal place to put top level navigation and Context Providers.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_3

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

import Home from "./pages/Home";
import Users from "./pages/Users";

const App = props => (
  <>
    <h1>My Site with lots of pages</h1>
    {props.children}
  </>
)

render(() => (
  <Router root={App}>
    <Route path="/users" component={Users} />
    <Route path="/" component={Home} />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Solid Router: `<A>` Component API Reference
DESCRIPTION: The `<A>` component in Solid Router functions similarly to an HTML `<a>` tag, providing automatic base path resolution, relative path support, and active/inactive class styling. It's used for client-side navigation and can be configured to match routes exactly or by prefix.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_41

LANGUAGE: APIDOC
CODE:

```
<A> Component:
  Description: Like the `<a>` tag but supports automatic apply of base path + relative paths and active class styling (requires client side JavaScript). The `<A>` tag has an `active` class if its href matches the current location, and `inactive` otherwise. Note: By default matching includes locations that are descendents (eg. href `/users` matches locations `/users` and `/users/123`), use the boolean `end` prop to prevent matching these. This is particularly useful for links to the root route `/` which would match everything.
  Props:
    href: string
      Description: The path of the route to navigate to. This will be resolved relative to the route that the link is in, but you can preface it with `/` to refer back to the root.
    noScroll: boolean
      Description: If true, turn off the default behavior of scrolling to the top of the new page
    replace: boolean
      Description: If true, don't add a new entry to the browser history. (By default, the new page will be added to the browser history, so pressing the back button will take you to the previous route.)
    state: unknown
      Description: Push this value to the history stack when navigating
    inactiveClass: string
      Description: The class to show when the link is inactive (when the current location doesn't match the link)
    activeClass: string
      Description: The class to show when the link is active
    end: boolean
      Description: If `true`, only considers the link to be active when the curent location matches the `href` exactly; if `false`, check if the current location _starts with_ `href`
```

---

TITLE: Basic usage of SolidJS `createAsync` primitive
DESCRIPTION: Demonstrates the fundamental usage of `createAsync`, a simplified async primitive that tracks like `createMemo` and converts a promise into a Signal. Reading it before it's ready triggers Suspense/Transitions.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_24

LANGUAGE: jsx
CODE:

```
const user = createAsync((currentValue) => getUser(params.id))
```

---

TITLE: Defining and Assigning a Preload Function in SolidJS Router
DESCRIPTION: Shows how to define a `preload` function for a SolidJS route, demonstrating its signature with `params` and `location` arguments, and how to assign it to a `Route` component to enable parallel data fetching.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_17

LANGUAGE: js
CODE:

```
import { lazy } from "solid-js";
import { Route } from "@solidjs/router";

const User = lazy(() => import("./pages/users/[id].js"));

// preload function
function preloadUser({params, location}) {
  // do preloading
}

// Pass it in the route definition
<Route path="/users/:id" component={User} preload={preloadUser} />;
```

---

TITLE: SolidJS Router: Defining and Using Actions
DESCRIPTION: Demonstrates how to define an `action` for data mutations and link it to HTML forms or buttons. It shows how to use `redirect` to navigate after a mutation, throwing a response to end execution.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_27

LANGUAGE: jsx
CODE:

```
import { action, revalidate, redirect } from "@solidjs/router"

// anywhere
const myAction = action(async (data) => {
  await doMutation(data);
  throw redirect("/", { revalidate: getUser.keyFor(data.id) }); // throw a response to do a redirect
});

// in component
<form action={myAction} method="post" />

//or
<button type="submit" formaction={myAction}></button>
```

---

TITLE: Retrieve Reactive Location Object (SolidJS Router)
DESCRIPTION: This hook provides a reactive `location` object, useful for accessing properties like `pathname`. It allows for dynamic updates based on route changes.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_46

LANGUAGE: js
CODE:

```
const location = useLocation();

const pathname = createMemo(() => parsePath(location.pathname));
```

---

TITLE: SolidJS Router: Using `useAction` Primitive
DESCRIPTION: Demonstrates how to use the `useAction` primitive to call actions directly from components, outside of a form context, allowing for custom data and type preservation.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_31

LANGUAGE: jsx
CODE:

```
// in component
const submit = useAction(myAction)
submit(...args)
```

---

TITLE: SolidJS Router: Using `redirect` Response Helper
DESCRIPTION: Shows how to use the `redirect` helper to force a navigation to a different route, typically by throwing it from a query or action function, indicating that the function's execution should end.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_33

LANGUAGE: js
CODE:

```
const getUser = query(() => {
  const user = await api.getCurrentUser()
  if (!user) throw redirect("/login");
  return user;
})
```

---

TITLE: SolidJS Router: Deleting Todo Item with FormData Action
DESCRIPTION: Illustrates how to create an action that processes `FormData` from a form to delete a todo item, emphasizing the use of hidden input fields for data transfer.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_28

LANGUAGE: js
CODE:

```
const deleteTodo = action(async (formData: FormData) => {
  const id = Number(formData.get("id"))
  await api.deleteTodo(id)
})

<form action={deleteTodo} method="post">
  <input type="hidden" name="id" value={todo.id} />
  <button type="submit">Delete</button>
</form>
```

---

TITLE: Solid Router: `<Navigate />` Component Usage
DESCRIPTION: The `<Navigate />` component in Solid Router provides immediate navigation to a specified path upon rendering. It uses the `href` prop, which can accept a string path or a function that dynamically determines the path based on `navigate` and `location` objects.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_42

LANGUAGE: jsx
CODE:

```
function getPath({ navigate, location }) {
  // navigate is the result of calling useNavigate(); location is the result of calling useLocation().
  // You can use those to dynamically determine a path to navigate to
  return "/some-path";
}

// Navigating to /redirect will redirect you to the result of getPath
<Route path="/redirect" component={() => <Navigate href={getPath} />} />;
```

---

TITLE: Correctly Handling Parent Routes with Nested Routes in SolidJS
DESCRIPTION: Illustrates how to correctly define a parent route (`/users`) alongside its nested child routes (`/:id`) in SolidJS, contrasting an incorrect approach with two working solutions to ensure both parent and child paths are routable.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_14

LANGUAGE: jsx
CODE:

```
//This won't work the way you'd expect
<Route path="/users" component={Users}>
  <Route path="/:id" component={User} />
</Route>

// This works
<Route path="/users" component={Users} />
<Route path="/users/:id" component={User} />

// This also works
<Route path="/users">
  <Route path="/" component={Users} />
  <Route path="/:id" component={User} />
</Route>
```

---

TITLE: Solid Router: `<Route>` Component API Reference
DESCRIPTION: The `<Route>` component is fundamental for defining route segments in Solid Router. It specifies the path, the component to render, and allows for nested routes and additional matching constraints.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_43

LANGUAGE: APIDOC
CODE:

```
<Route> Component:
  Description: The Component for defining Routes.
  Props:
    path: string
      Description: Path partial for defining the route segment
    component: Component
      Description: Component that will be rendered for the matched segment
    matchFilters: MatchFilters
      Description: Additional constraints for matching against the route
    children: JSX.Element
      Description: Nested `<Route>` definitions
    preload: RoutePreloadFunc
      Description: Function called during preload or when the route is navigated to.
```

---

TITLE: Solid Router Component API Reference
DESCRIPTION: Detailed API documentation for the main <Router> component in SolidJS, listing its props, their types, and descriptions. This component is essential for browser-based routing.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_40

LANGUAGE: APIDOC
CODE:

```
<Router> Component:
  prop: children
    type: JSX.Element | RouteDefinition | RouteDefinition[]
    description: The route definitions
  prop: root
    type: Component
    description: Top level layout component
  prop: base
    type: string
    description: Base url to use for matching routes
  prop: actionBase
    type: string
    description: Root url for server actions, default: /_server
  prop: preload
    type: boolean
    description: Enables/disables preloads globally, default: true
  prop: explicitLinks
    type: boolean
    description: Disables all anchors being intercepted and instead requires <A>. Default: false. (To disable interception for a specific link, set target to any value, e.g. <a target="_self">.)
```

---

TITLE: Implement Server-Side Rendering (SSR) with Solid Router
DESCRIPTION: Demonstrates how to configure Solid Router for Server-Side Rendering (SSR) by passing the request URL to the <Router> component, allowing it to handle routing on the server.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_39

LANGUAGE: jsx
CODE:

```
import { isServer } from "solid-js/web";
import { Router } from "@solidjs/router";

<Router url={isServer ? req.url : ""} />;
```

---

TITLE: Validate Dynamic Route Parameters with MatchFilters in SolidJS
DESCRIPTION: Illustrates how to use `matchFilters` prop on a `Route` to validate path parameters. Filters can be defined as arrays for enum values, regular expressions, or custom functions, ensuring only valid URLs match the route. If validation fails, the route will not match.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_9

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";
import type { SegmentValidators } from "./types";

const User = lazy(() => import("./pages/User"));

const filters: MatchFilters = {
  parent: ["mom", "dad"], // allow enum values
  id: /^\d+$/, // only allow numbers
  withHtmlExtension: (v: string) => v.length > 5 && v.endsWith(".html"), // we want an `*.html` extension
};

render(() => (
  <Router>
    <Route
      path="/users/:parent/:id/:withHtmlExtension"
      component={User}
      matchFilters={filters}
    />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Intercept Route Changes with useBeforeLeave (SolidJS Router)
DESCRIPTION: This hook takes a function that executes before a route change occurs. The function receives arguments including `from`, `to`, `options`, `preventDefault` to block the change, `defaultPrevented` status, and `retry` to re-attempt navigation, optionally skipping further handlers. It's ideal for confirming unsaved changes.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_52

LANGUAGE: js
CODE:

```
useBeforeLeave((e: BeforeLeaveEventArgs) => {
  if (form.isDirty && !e.defaultPrevented) {
    // preventDefault to block immediately and prompt user async
    e.preventDefault();
    setTimeout(() => {
      if (window.confirm("Discard unsaved changes - are you sure?")) {
        // user wants to proceed anyway so retry with force=true
        e.retry(true);
      }
    }, 100);
  }
});
```

---

TITLE: SolidJS Router: `Submission` Type and `useSubmission` Usage
DESCRIPTION: Provides the TypeScript type definition for `Submission`, representing the state of an in-flight action, and demonstrates how `useSubmission` and `useSubmissions` are used to inject optimistic updates.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_32

LANGUAGE: typescript
CODE:

```
type Submission<T, U> = {
  readonly input: T;
  readonly result?: U;
  readonly pending: boolean;
  readonly url: string;
  clear: () => void;
  retry: () => void;
};
```

LANGUAGE: jsx
CODE:

```
const submissions = useSubmissions(action, (input) => filter(input));
const submission = useSubmission(action, (input) => filter(input));
```

---

TITLE: Define Optional Route Parameters in SolidJS Router
DESCRIPTION: Shows how to make a path parameter optional by appending a question mark (`?`) to its name. This allows the route to match URLs both with and without the specified parameter, such as `/stories` and `/stories/123`.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_10

LANGUAGE: jsx
CODE:

```
// Matches stories and stories/123 but not stories/123/comments
<Route path="/stories/:id?" component={Stories} />
```

---

TITLE: SolidJS Router: Using `reload` Response Helper
DESCRIPTION: Demonstrates how to use the `reload` helper to re-fetch data on the current page, often with a `revalidate` hint to specify which data keys should be invalidated and reloaded after an action completes.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_34

LANGUAGE: js
CODE:

```
const getTodo = query(async (id: number) => {
  const todo = await fetchTodo(id);
  return todo;
}, "todo")

const updateTodo = action(async (todo: Todo) => {
  await updateTodo(todo.id, todo);
  reload({ revalidate: getTodo.keyFor(id) })
})
```

---

TITLE: Determine Path Match with useMatch (SolidJS Router)
DESCRIPTION: `useMatch` takes an accessor that returns a path and creates a Memo. This Memo returns match information if the current path matches the provided path, making it useful for conditional rendering based on route matching.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_49

LANGUAGE: js
CODE:

```
const match = useMatch(() => props.href);

return <div classList={{ active: Boolean(match()) }} />;
```

---

TITLE: Lazy-load Route Components in Solid Router
DESCRIPTION: This way, the `Users` and `Home` components will only be loaded if you're navigating to `/users` or `/`, respectively.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_5

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } => "solid-js/web";
import { Router, Route } from "@solidjs/router";

const Users = lazy(() => import("./pages/Users"));
const Home = lazy(() => import("./pages/Home"));

const App = props => (
  <>
    <h1>My Site with lots of pages</h1>
    {props.children}
  </>
)

render(() => (
  <Router root={App}>
    <Route path="/users" component={Users} />
    <Route path="/" component={Home} />
  </Router>
), document.getElementById("app"));
```

---

TITLE: Exporting and Importing SolidJS Preload Functions
DESCRIPTION: Demonstrates a common pattern for organizing SolidJS preload functions by exporting them from a dedicated data file (`route.data.js`) and then importing them into the route definition for better modularity.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_19

LANGUAGE: js
CODE:

```
import { lazy } from "solid-js";
import { Route } from "@solidjs/router";
import preloadUser from "./pages/users/[id].data.js";
const User = lazy(() => import("/pages/users/[id].js"));

// In the Route definition
<Route path="/users/:id" component={User} preload={preloadUser} />;
```

---

TITLE: Implement Wildcard Routes in SolidJS Router
DESCRIPTION: Explains how to use a wildcard (`*`) to match any subsequent part of a path. The wildcard can be named (e.g., `*any`) to expose the matched segment as a parameter to the component. The wildcard token must be the last part of the path.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_11

LANGUAGE: jsx
CODE:

```
// Matches any path that begins with foo, including foo/, foo/a/, foo/a/b/c
<Route path="foo/*" component={Foo} />

// If you want to expose the wild part of the path to the component as a parameter, you can name it:
<Route path="foo/*any" component={Foo} />
```

---

TITLE: Retrieve All Current Route Matches (SolidJS Router)
DESCRIPTION: This hook returns all the matches for the currently matched route. It is useful for accessing comprehensive route information, such as extracting breadcrumbs from route definitions.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_50

LANGUAGE: js
CODE:

```
const matches = useCurrentMatches();

const breadcrumbs = createMemo(() => matches().map(m => m.route.info.breadcrumb));
```

---

TITLE: Define Multiple Paths for a Single Route in SolidJS Router
DESCRIPTION: Demonstrates how to assign an array of paths to a single `Route` component. This allows a route to remain mounted and not re-render when switching between two or more locations that it matches, improving performance for related routes.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_12

LANGUAGE: jsx
CODE:

```
// Navigating from login to register does not cause the Login component to re-render
<Route path={["login", "register"]} component={Login} />
```

---

TITLE: Access SolidJS `query` keys for invalidation
DESCRIPTION: Explains how to retrieve the base query key and a specific entry's key using `getUser.key` and `getUser.keyFor(id)`. These methods are crucial for selectively invalidating cached query data.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_23

LANGUAGE: ts
CODE:

```
let id = 5;

getUser.key // returns "users"
getUser.keyFor(id) // returns "users[5]"
```

---

TITLE: SolidJS Router v0.10.0 Migration: Removed APIs (APIDOC)
DESCRIPTION: Details the significant API changes in SolidJS Router v0.10.0, specifically the removal of `<Outlet>`, `<Routes>`, and `useRoutes`. These components are no longer used due to changes supporting Islands/Partial Hydration, with `props.children` now handling outlets and `<Router>` acting as the primary route container.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_54

LANGUAGE: APIDOC
CODE:

```
<Outlet>, <Routes>, useRoutes:
  - No longer used; replaced by `props.children` for outlets.
  - Nested `<Routes>` components are removed.
  - `<Router>` now acts as the `<Routes>` component, accepting only `<Route>` children.
  - Top-level layout should be in the `root` prop of the router.
```

---

TITLE: SolidJS Router v0.10.0 Migration: `element` prop removed from `Route` (APIDOC)
DESCRIPTION: Explains the removal of the `element` prop from the `Route` component in SolidJS Router v0.10.0. This change simplifies route definition by removing a redundant way to define route components, especially since outlets are now handled manually.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_55

LANGUAGE: APIDOC
CODE:

```
element prop removed from Route:
  - No longer needed as outlets are passed manually.
  - Reduces confusion and edge cases by having a single way to define route components.
```

---

TITLE: Check Routing Transition State with useIsRouting (SolidJS Router)
DESCRIPTION: This hook returns a signal indicating if the route is currently in a Transition. It's useful for displaying stale or pending states during concurrent rendering when route resolution is suspended.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_48

LANGUAGE: js
CODE:

```
const isRouting = useIsRouting();

return (
  <div classList={{ "grey-out": isRouting() }}>
    <MyAwesomeContent />
  </div>
);
```

---

TITLE: Basic usage of SolidJS `createAsyncStore` primitive
DESCRIPTION: Illustrates the basic usage of `createAsyncStore`, which is similar to `createAsync` but creates a deeply reactive store. It is ideal for managing large model data that requires fine-grained updates.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_26

LANGUAGE: jsx
CODE:

```
const todos = createAsyncStore(() => getTodos());
```

---

TITLE: Use Memory Mode Router for Testing in SolidJS
DESCRIPTION: Illustrates the usage of <MemoryRouter> for testing purposes, providing an in-memory routing environment without interacting with the browser's URL.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_38

LANGUAGE: jsx
CODE:

```
import { MemoryRouter } from "@solidjs/router";

<MemoryRouter />;
```

---

TITLE: SolidJS Router: Using Action's `with` Method for Typed Data
DESCRIPTION: Shows how to simplify action calls by using the `.with()` method, which pre-applies arguments, making it easier to pass typed data directly without relying on `FormData` and hidden fields.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_29

LANGUAGE: js
CODE:

```
const deleteUser = action(api.deleteTodo)

<form action={deleteTodo.with(todo.id)} method="post">
  <button type="submit">Delete</button>
</form>
```

---

TITLE: Force Re-render of SolidJS Route Component
DESCRIPTION: Provides a tip on how to force a re-render for routes that share the same path match by wrapping the component in a keyed `<Show>` component.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_8

LANGUAGE: jsx
CODE:

```
<Show when={params.something} keyed><MyComponent></Show>
```

---

TITLE: Manually Preload a Route (SolidJS Router)
DESCRIPTION: `usePreloadRoute` returns a function that allows for manual preloading of a route. This functionality is similar to automatic preloading triggered by link hovering but is exposed as an explicit API for programmatic control.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_51

LANGUAGE: js
CODE:

```
const preload = usePreloadRoute();

preload(`/users/settings`, { preloadData: true });
```

---

TITLE: SolidJS Router: Naming Actions for SSR Compatibility
DESCRIPTION: Explains how to provide a unique name to an action as a second argument, which is crucial for maintaining stable references and ensuring proper serialization across server-side rendering.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_30

LANGUAGE: jsx
CODE:

```
const myAction = action(async (args) => {}, "my-action");
```

---

TITLE: Defining Equivalent Nested Routes in SolidJS
DESCRIPTION: Demonstrates two equivalent ways to define a nested route in SolidJS, showing that a single flat route can be expressed hierarchically using nested `<Route>` components.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_13

LANGUAGE: jsx
CODE:

```
<Route path="/users/:id" component={User} />
```

LANGUAGE: jsx
CODE:

```
<Route path="/users">
  <Route path="/:id" component={User} />
</Route>
```

---

TITLE: Demonstrating Indefinite Nested Routes in SolidJS
DESCRIPTION: Illustrates how SolidJS allows for indefinitely nested routes, emphasizing that only leaf nodes create actual routes, while parent components can render children within their structure, creating a nested visual hierarchy.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_16

LANGUAGE: jsx
CODE:

```
<Route
  path="/"
  component={(props) =>
    <div>
      Onion starts here {props.children}
    </div>
  }
>
  <Route
    path="layer1"
    component={(props) =>
      <div>
        Another layer {props.children}
      </div>
    }
  >
    <Route
      path="layer2"
      component={() => <div>Innermost layer</div>}
    />
  </Route>
</Route>
```

---

TITLE: Use Hash Mode Router in SolidJS
DESCRIPTION: Explains how to switch Solid Router to hash mode by using the <HashRouter> component, which utilizes location.hash for routing instead of location.pathname.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_37

LANGUAGE: jsx
CODE:

```
import { HashRouter } from "@solidjs/router";

<HashRouter />;
```

---

TITLE: SolidJS Router Preload Function Parameters
DESCRIPTION: Documents the parameters passed to a SolidJS Router preload function, including `params`, `location`, and `intent`, with their types and descriptions, explaining the context of the preload call.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_18

LANGUAGE: APIDOC
CODE:

```
preloadFunction(args: object)
  args:
    params: object - The route parameters (same value as calling `useParams()` inside the route component)
    location: { pathname: string, search: string, hash: string, query: object, state: any, key: string } - An object that you can use to get more information about the path (corresponds to `useLocation()`)
    intent: "initial" | "navigate" | "native" | "preload" - Indicates why this function is being called.
      "initial" - the route is being initially shown (ie page load)
      "native" - navigate originated from the browser (eg back/forward)
      "navigate" - navigate originated from the router (eg call to navigate or anchor clicked)
      "preload" - not navigating, just preloading (eg link hover)
```

---

TITLE: useBeforeLeave Callback Parameters (SolidJS Router APIDOC)
DESCRIPTION: Documentation for the parameters passed to the callback function of `useBeforeLeave`. These parameters provide context about the navigation attempt and control over its prevention or retry.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_53

LANGUAGE: APIDOC
CODE:

```
from (_Location_): current location (before change).
to (_string | number_): path passed to `navigate`.
options (_NavigateOptions_): options passed to `navigate`.
preventDefault (_function_): call to block the route change.
defaultPrevented (_readonly boolean_): `true` if any previously called leave handlers called `preventDefault`.
retry (_function_, _force?: boolean_ ): call to retry the same navigation, perhaps after confirming with the user. Pass `true` to skip running the leave handlers again (i.e. force navigate without confirming).
```

---

TITLE: Configure Solid Router with Single Route Definition Object
DESCRIPTION: Shows how to define a single route by passing a RouteDefinition object directly to the <Router> component, useful for simple applications or a single entry point.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_36

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router } from "@solidjs/router";

const route = {
  path: "/",
  component: lazy(() => import("/pages/index.js"))
};

render(() => <Router>{route}</Router>, document.getElementById("app"));
```

---

TITLE: Access `latest` field with SolidJS `createAsync`
DESCRIPTION: Shows how to access the `latest` field on a `createAsync` signal, which preserves the last successfully resolved value. This field is useful for displaying stale data while new data is loading, though it will be removed in future versions.
SOURCE: https://github.com/solidjs/solid-router/blob/main/README.md#_snippet_25

LANGUAGE: jsx
CODE:

```
const user = createAsync((currentValue) => getUser(params.id))
return <h1>{user.latest.name}</h1>;
```
