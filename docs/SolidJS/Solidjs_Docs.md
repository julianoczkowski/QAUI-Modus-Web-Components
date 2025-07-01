TITLE: Update SolidJS Stores with `produce` Utility
DESCRIPTION: `produce` allows working with store data as if it were a mutable JavaScript object, enabling multiple property changes simultaneously. It creates a new immutable version of the store after changes. Note that `produce` is designed for arrays and objects, not JavaScript Sets or Maps.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_15

LANGUAGE: jsx
CODE:

```
import { produce } from "solid-js/store"

// without produce
setStore("users", 0, "username", "newUsername")
setStore("users", 0, "location", "newLocation")

// with produce
setStore(
	"users",
	0,
	produce((user) => {
		user.username = "newUsername"
		user.location = "newLocation"
	})
)
```

---

TITLE: Install Solid Router Package
DESCRIPTION: This snippet shows how to install the `@solidjs/router` package using a package manager. This package is not included by default and is required for routing functionality.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/routing-and-navigation.mdx#_snippet_0

LANGUAGE: shell
CODE:

```
@solidjs/router
```

---

TITLE: SolidJS Synchronous Reactivity Example with createEffect
DESCRIPTION: This snippet demonstrates SolidJS's default synchronous reactivity. When `count` changes, the `createEffect` immediately updates `double` by multiplying `count()` by 2. This ensures `double` is always consistent with the latest `count` value in a predictable, ordered manner.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/intro-to-reactivity.mdx#_snippet_8

LANGUAGE: jsx
CODE:

```
const [count, setCount] = createSignal(0);
const [double, setDouble] = createSignal(0);

createEffect(() => {
	setDouble(count() * 2);
});
```

---

TITLE: SolidJS query Function Usage Example
DESCRIPTION: Demonstrates how to define and use a `query` function to fetch user data. It illustrates how `query` caches results for identical arguments and triggers new fetches for different arguments or after a cache expiration timeout.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/data-apis/query.mdx#_snippet_0

LANGUAGE: js
CODE:

```
const getUser = query(
	(id, options = {}) =>
		fetch(`/api/users/${id}?summary=${options.summary || false}`).then((r) =>
			r.json()
		),
	"usersById"
);

getUser(123); // Causes a GET request to /api/users/123?summary=false
getUser(123); // Does not cause a GET request
getUser(123, { summary: true }); // Causes a GET request to /api/users/123?summary=true
setTimeout(() => getUser(123, { summary: true }), 999000); // Eventually causes another GET request to /api/users/123?summary=true
```

---

TITLE: Dynamically Assign Values with setStore in SolidJS
DESCRIPTION: Shows how to use a function as the value argument in `setStore`. This function receives the old value, allowing you to compute and assign a new value dynamically based on the existing one, which is useful for complex transformations like toggling a boolean.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_12

LANGUAGE: jsx
CODE:

```
setStore("users", 3, "loggedIn" , (loggedIn) => !loggedIn)
```

---

TITLE: Initialize Solid Router in a SolidJS application
DESCRIPTION: Demonstrates how to import the `Router` component from `@solidjs/router` and render it as the root component of a SolidJS application. This setup enables the routing mechanism to match URLs and render appropriate routes.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/getting-started/installation-and-setup.mdx#_snippet_1

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import { Router } from "@solidjs/router";

const wrapper = document.getElementById("app");

if (!wrapper) {
  throw new Error("Wrapper div not found");
}

render(() => <Router />, wrapper)
```

---

TITLE: SolidJS Effect Observing Multiple Signals
DESCRIPTION: Demonstrates an effect observing multiple signals (`count` and `message`). The effect's callback runs whenever _any_ of the observed signals change, logging the current values of all signals, showcasing how effects react to changes in multiple dependencies.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/effects.mdx#_snippet_3

LANGUAGE: jsx
CODE:

```
import { createSignal, createEffect } from "solid-js";

const [count, setCount] = createSignal(0);
const [message, setMessage] = createSignal("Hello");

createEffect(() => {
	console.log(count(), message());
});

setCount(1); // Output: 1, "Hello"
setMessage("World"); // Output: 1, "World"
```

---

TITLE: Using Solid Router's <A> component for navigation
DESCRIPTION: This example illustrates the use of Solid Router's dedicated `<A>` component for navigation. Unlike standard `<a>` tags, the `<A>` component automatically handles base URLs and relative paths, simplifying route management and providing a more integrated solution within SolidJS applications.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/getting-started/linking-routes.mdx#_snippet_1

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router, Route, A } from "@solidjs/router";

const Users = lazy(() => import("./pages/Users"));
const Home = lazy(() => import("./pages/Home"));

const App = (props) => (
	<>
		<nav>
			<A href="/users">Users</A>
			<A href="/">Home</A>
		</nav>
		<h1>My Site with lots of pages</h1>
		{props.children}
	</>
);

render(
	() => (
		<Router root={App}>
			<Route path="/users" component={Users} />
			<Route path="/" component={Home} />
		</Router>
	),
	document.getElementById("app")
);
```

---

TITLE: SolidJS Counter Component with Reactive Signal
DESCRIPTION: This SolidJS component demonstrates basic reactivity using `createSignal` to manage a counter. Clicking the button increments the count, and only the displayed number updates, showcasing efficient UI synchronization without full component re-renders.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/intro-to-reactivity.mdx#_snippet_0

LANGUAGE: jsx
CODE:

```
function Counter() {
	const [count, setCount] = createSignal(0);
	const increment = () => setCount((prev) => prev + 1);

	return (
		<div>
			<span>Count: {count()}</span>{" "}
			<button type="button" onClick={increment}>
				Increment
			</button>
		</div>
	);
}
```

---

TITLE: SolidJS Component using createAsync
DESCRIPTION: This snippet demonstrates how to use `createAsync` within a SolidJS component to fetch user data asynchronously. It integrates with `Suspense` to show a loading state while the data is being fetched.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/data-apis/create-async.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
import { createAsync } from "@solidjs/router";
import { Suspense } from "solid-js";
import { getUser } from "./api";

export function Component () => {
	const user = createAsync(() => getUser(params.id));

	return (
		<Suspense fallback="loading user...">
			<p>{user()}</p>
		</Suspense>
	);
}
```

---

TITLE: Appending Elements to SolidJS Store Arrays with Path Syntax
DESCRIPTION: Demonstrates two flexible ways to append new elements to an array within a SolidJS store using path syntax. It shows the traditional spread operator approach and a more concise method where the array's current length is used as the index to directly set the new element.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_8

LANGUAGE: jsx
CODE:

```
setStore("users", (otherUsers) => [
	...otherUsers,
	{
		id: 3,
		username: "michael584",
		location: "Nigeria",
		loggedIn: false,
	},
])

// can become

setStore("users", store.users.length, {
	id: 3,
	username: "michael584",
	location: "Nigeria",
	loggedIn: false,
})
```

---

TITLE: Accessing Props in a Child Component in SolidJS
DESCRIPTION: Shows how a child component can access the passed properties via the `props` object in SolidJS.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/props.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
function MyComponent(props) {
	return <div>Hello {props.name}</div>;
}
```

---

TITLE: Fetch Data Dynamically with createResource and useParams in SolidJS
DESCRIPTION: This snippet combines `useParams` with SolidJS's `createResource` to fetch data dynamically based on changing route parameters. It illustrates how `fetchUser` is called every time the `id` parameter changes, providing a reactive way to load user data from an API.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/routing-and-navigation.mdx#_snippet_10

LANGUAGE: jsx
CODE:

```
import { createResource } from "solid-js";
import { useParams } from "@solidjs/router";

async function fetchUser(id) {
	const response = await fetch(
		`https://jsonplaceholder.typicode.com/users/${id}`
	);
	return response.json();
}

const User = () => {
	const params = useParams();
	const [data] = createResource(() => params.id, fetchUser); // Pass the id parameter to createResource

	return (
		<div>
			<Show when={!data.loading} fallback={<p>Loading...</p>}>
				<div>
					<p>Name: {data().name}</p>
					<p>Email: {data().email}</p>
					<p>Phone: {data().phone}</p>
				</div>
			</Show>
		</div>
	);
};
```

---

TITLE: Accessing and Updating SolidJS Signal Values
DESCRIPTION: This example illustrates how to interact with a SolidJS signal. The getter function `count()` retrieves the signal's current value, while the setter `setCount(value)` updates it, demonstrating the immediate change in the signal's state.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/intro-to-reactivity.mdx#_snippet_2

LANGUAGE: js
CODE:

```
console.log(count()); // `count()` is a getter that returns the current value of `count`, which is `0`.

setCount(1); // the setter, `setCount`, updates the value of `count`.

console.log(count()); // the updated value of `count` is now `1`.
```

---

TITLE: SolidStart Server-Side Data Loading with "use server"
DESCRIPTION: This code demonstrates how to implement server-side data loading in SolidStart using the "use server" directive within a query function. The getUsers function, marked with "use server", fetches user data from a store.users.list() call, which runs only on the server. The createAsync hook then consumes this data on the client, making it available for rendering. This pattern is ideal for accessing server-only resources like databases or internal APIs directly from your SolidStart components.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/building-your-application/data-loading.mdx#_snippet_2

LANGUAGE: tsx
CODE:

```
// /routes/users.tsx
import { For } from "solid-js";
import { createAsync, query } from "@solidjs/router";

type User = { name: string; email: string };

const getUsers = query(async () => {
	"use server";
	return store.users.list();
}, "users");

export const route = {
	preload: () => getUsers()
};

export default function Page() {
	const users = createAsync(() => getUsers());

	return <For each={users()}>{(user) => <li>{user.name}</li>}</For>;
}
```

LANGUAGE: jsx
CODE:

```
// /routes/users.jsx
import { For } from "solid-js";
import { createAsync, query } from "@solidjs/router";

const getUsers = query(async () => {
	"use server";
	return store.users.list();
}, "users");

export const route = {
	preload: () => getUsers()
};

export default function Page() {
	const users = createAsync(() => getUsers());

	return <For each={users()}>{(user) => <li>{user.name}</li>}</For>;
}
```

---

TITLE: SolidJS Signal Not Tracked Outside Reactive Scope
DESCRIPTION: This example demonstrates that a signal accessed outside a tracking scope (like `createEffect`) will not trigger updates. The `console.log` only reflects the initial value, as it's a one-time event and not subscribed to changes.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/intro-to-reactivity.mdx#_snippet_4

LANGUAGE: jsx
CODE:

```
const [count, setCount] = createSignal(0);

console.log("Count:", count());

setCount(1);

// Output: Count: 0

// `count` is not being tracked, so the console log will not update when `count` changes.
```

---

TITLE: SolidJS `on` Basic Usage with `createEffect`
DESCRIPTION: Demonstrates how `on` explicitly manages dependencies within `createEffect`, showing its functional equivalence to manually tracking a dependency and using `untrack` for other values.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/reactive-utilities/on-util.mdx#_snippet_1

LANGUAGE: typescript
CODE:

```
createEffect(on(a, (v) => console.log(v, b())));

// is equivalent to:
createEffect(() => {
	const v = a();
	untrack(() => console.log(v, b()));
});
```

---

TITLE: SolidJS Index Component Item as Signal Example
DESCRIPTION: Demonstrates how the `item` argument within the `<Index>` component's callback is a signal, allowing its content to change without re-rendering the entire list. The example accesses `item().name` and `item().completed`.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/control-flow/list-rendering.mdx#_snippet_3

LANGUAGE: jsx
CODE:

```
import { Index } from "solid-js"

<Index each={data()}>
	{(item, index) => (
		<li>
			{item().name} - {item().completed}
		</li>
	)}
</Index>
```

---

TITLE: SolidJS Suspense Component Type Definition
DESCRIPTION: Defines the TypeScript interface for the SolidJS `Suspense` component, specifying its `fallback` (optional JSX element for loading state) and `children` (the content to be rendered) props, and its return type as a JSX element.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/components/suspense.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
import { Suspense } from "solid-js"
import type { JSX } from "solid-js"

function Suspense(props: {
	fallback?: JSX.Element
	children: JSX.Element
}): JSX.Element
```

---

TITLE: SolidStart APIEvent Object Reference
DESCRIPTION: Defines the structure and properties of the `APIEvent` object, which is passed as the first argument to SolidStart API route handlers. It includes details on the `request`, `params`, and `fetch` properties.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/building-your-application/api-routes.mdx#_snippet_3

LANGUAGE: APIDOC
CODE:

```
APIEvent object:
  request: Request object representing the request sent by the client.
  params: Object that contains the dynamic route parameters.
    Example: If the route is `/api/users/:id`, and the request is made to `/api/users/123`, then `params` will be `{ id: 123 }`.
  fetch: An internal `fetch` function that can be used to make requests to other API routes without worrying about the `origin` of the URL.
```

---

TITLE: Install SolidJS Meta Package
DESCRIPTION: Instructions for installing the `@solidjs/meta` package using your preferred package manager. This package is essential for managing HTML head elements in SolidJS applications. Note the prerequisites for SolidJS versions: `v1.0` requires `0.27.x+`, while `v0.x` requires `v0.26.x`.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-meta/getting-started/installation-and-setup.mdx#_snippet_0

LANGUAGE: shell
CODE:

```
@solidjs/meta
```

---

TITLE: Revalidate Specific Cached Functions in SolidJS
DESCRIPTION: This snippet demonstrates how to manually revalidate specific cached functions in SolidJS. It uses the `revalidate` helper with an array of keys, allowing targeted data refresh for `getTodos` and `getTodoByID`.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/data-apis/action.mdx#_snippet_10

LANGUAGE: jsx
CODE:

```
revalidate([getTodos.key, getTodoByID.keyFor(id)])
```

---

TITLE: SolidJS Directive Function Signature
DESCRIPTION: Defines the required function signature for a SolidJS directive, including the DOM element it's applied to and an accessor function for its passed values. Directives are called at render time, before the element is added to the DOM, ensuring elements are fully primed.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/refs.mdx#_snippet_6

LANGUAGE: typescript
CODE:

```
function directive(element: Element, accessor: () => any): void
```

---

TITLE: SolidJS createUniqueId Basic Usage
DESCRIPTION: Illustrates a simple call to `createUniqueId` to assign a unique identifier to a constant. On the server, this function requires hydratable components to function correctly.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/component-apis/create-unique-id.mdx#_snippet_1

LANGUAGE: ts
CODE:

```
const id = createUniqueId()
```

---

TITLE: Reading and Writing SolidJS Signals
DESCRIPTION: Illustrates various ways to interact with SolidJS signals, including reading their current value, creating derived computations, building tracking scopes, and updating values using both direct assignment and functional setters.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/basic-reactivity/create-signal.mdx#_snippet_2

LANGUAGE: tsx
CODE:

```
// read signal's current value, and
// depend on signal if in a tracking scope
// (but nonreactive outside of a tracking scope):
const currentCount = count()

// or wrap any computation with a function,
// and this function can be used in a tracking scope:
const doubledCount = () => 2 * count()

// or build a tracking scope and depend on signal:
const countDisplay = <div>{count()}</div>

// write signal by providing a value:
setReady(true)

// write signal by providing a function setter:
const newCount = setCount((prev) => prev + 1)
```

---

TITLE: SolidJS query Function Arguments API
DESCRIPTION: Defines the parameters required by the `query` higher-order function. It specifies the function to be cached (`fn`) and a unique string name for the query key (`name`).
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/data-apis/query.mdx#_snippet_3

LANGUAGE: APIDOC
CODE:

```
query(fn, name): CachedFunction
  fn: (...args: any) => any
    description: A function whose return value you'd like to be cached.
  name: string
    description: Any arbitrary string that you'd like to use as the rest of the query key.
    note: Since the internal cache is shared by all the functions using `query`, the string should be unique for each function passed to `query`. If the same key is used with multiple functions, one function might return the cached result of the other.
```

---

TITLE: Create and manage a session with useSession in TypeScript
DESCRIPTION: This TypeScript example demonstrates how to use the `useSession` helper from `vinxi/http` to create and manage a server-side session. It shows how to define session data types, initialize a session with a strong password (from environment variables) and a custom name, and update session data if a default value is needed. This helper adds a `Set-Cookie` HTTP header to the server response.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/advanced/session.mdx#_snippet_0

LANGUAGE: typescript
CODE:

```
import { useSession } from "vinxi/http";

type SessionData = {
	theme: "light" | "dark";
};

export async function useThemeSession() {
	"use server";
	const session = await useSession<SessionData>({
		password: process.env.SESSION_SECRET as string,
		name: "theme"
	});

	if (!session.data.theme) {
		await session.update({
			theme: "light"
		});
	}

	return session;
}
```

---

TITLE: Using Solid Router Actions in Components
DESCRIPTION: This example illustrates how to integrate and invoke a defined action within a Solid component. It uses the `useAction` hook to obtain a callable reference to the `echo` action, which then processes the provided message.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/concepts/actions.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
import { action, useAction } from "@solidjs/router";

const echo = action(async (message: string) => {
  await new Promise((resolve, reject) => setTimeout(resolve, 1000));
  console.log(message);
});

export function MyComponent() {
  const myEcho = useAction(echo);

  myEcho("Hello from Solid!");
}
```

---

TITLE: Using getServerFunctionMeta in SolidJS Server Functions
DESCRIPTION: This snippet demonstrates how to use `getServerFunctionMeta` within a SolidJS server function to obtain a unique, stable ID for the function's execution context. This ID can be used to manage in-memory state (like a counter) that persists across parallel instances but resets on new builds. It shows importing the function and using the `id` property to create a unique key for an application cache.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/reference/server/get-server-function-meta.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
import { getServerFunctionMeta } from "@solidjs/start";

// or some in-memory db
const appCache: any = globalThis;

const counter = async () => {
	"use server";
	const { id } = getServerFunctionMeta()!;
	const key = `counter_${id}`;
	appCache[key] = appCache[key] ?? 0;
	appCache[key]++;

	return appCache[key] as number;
};
```

---

TITLE: SolidJS Show Component with Fallback Content
DESCRIPTION: Illustrates how to use the `fallback` property with the `<Show>` component in SolidJS. When the `when` condition is false, the content specified in `fallback` is rendered instead of the children.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/control-flow/conditional-rendering.mdx#_snippet_1

LANGUAGE: jsx
CODE:

```
import { Show } from "solid-js"

<Show when={!data.loading} fallback={<div>Loading...</div>}>
	<h1>Hi, I am {data().name}.</h1>
</Show>
```

---

TITLE: Scoped Styling with CSS Modules in SolidStart
DESCRIPTION: Explains how to implement scoped CSS styles using Vite's CSS Modules feature in SolidStart. This involves naming CSS files with .module.css and importing the generated class names into the component to prevent naming conflicts and ensure unique styling.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/building-your-application/css-and-styling.mdx#_snippet_1

LANGUAGE: css
CODE:

```
.card {
  background-color: #446b9e;
}

div.card > h1 {
  font-size: 1.5em;
  font-weight: bold;
}

div.card > p {
  font-size: 1em;
  font-weight: normal;
}
```

LANGUAGE: jsx
CODE:

```
import styles from "./Card.module.css";

const Card = (props) => {
  return (
    <div class={styles.card}>
      <h1>{props.title}</h1>
      <p>{props.text}</p>
    </div>
  );
};
```

---

TITLE: SolidJS Router: Update Todo with Reload Action
DESCRIPTION: This TypeScript snippet demonstrates how to use the `reload` helper within a SolidJS Router action. It updates a todo item in the database and then invalidates a specific query key (`getTodo.keyFor(id)`) to trigger a re-fetch of related data, ensuring the UI reflects the latest changes.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/response-helpers/reload.mdx#_snippet_0

LANGUAGE: ts
CODE:

```
import { action, reload } from "@solidjs/router";
import { putTodo, getTodo } from "../db";

const updateTodo = action(async (todo: Todo) => {
	await putTodo(todo.id, todo);

  return reload({ revalidate: getTodo.keyFor(id) });
});
```

---

TITLE: SolidJS: Handling Side Effects with createEffect
DESCRIPTION: Shows the recommended approach for managing side effects in SolidJS applications. By using `createEffect` for side effects, the `createMemo` remains pure, preventing reactivity issues and maintaining a clear separation of concerns.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/derived-values/memos.mdx#_snippet_3

LANGUAGE: jsx
CODE:

```
import { createSignal, createMemo, createEffect } from "solid-js"

const [count, setCount] = createSignal(0)
const [message, setMessage] = createSignal("")

const isEven = createMemo(() => count() % 2 === 0)

createEffect(() => {
	if (count() > 10) {
		setMessage("Count is too high!")
	}
})
```

---

TITLE: Authenticate Zerops CLI
DESCRIPTION: After generating an access token from the Zerops app settings, use this command to log into the Zerops CLI. Replace <token> with your actual access token.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/deployment-options/zerops.mdx#_snippet_5

LANGUAGE: bash
CODE:

```
zcli login <token>
```

---

TITLE: SolidJS useContext Basic Consumption
DESCRIPTION: Demonstrates the fundamental way to consume context using `useContext` in SolidJS. It shows how to destructure state and actions directly from a `CounterContext` instance, allowing access to shared data and functions within a component's scope.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/component-apis/use-context.mdx#_snippet_0

LANGUAGE: ts
CODE:

```
const [state, { increment, decrement }] = useContext(CounterContext)
```

---

TITLE: SolidJS onCleanup for Resource Disposal
DESCRIPTION: The `onCleanup` function in SolidJS is used to perform cleanup tasks when a component unmounts. It helps prevent memory leaks by clearing subscriptions, intervals, or other references that might otherwise continue running in the background after the component is no longer active. This ensures proper resource management.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/effects.mdx#_snippet_7

LANGUAGE: jsx
CODE:

```
import { onCleanup } from "solid-js";

function App() {
	const [count, setCount] = createSignal(0);

	const timer = setInterval(() => {
		setCount((prev) => prev + 1);
	}, 1000);

	onCleanup(() => {
		clearInterval(timer);
	});

	return <div>Count: {count()}</div>;
}
```

---

TITLE: SolidJS: createRenderEffect Function Arguments
DESCRIPTION: Provides a detailed description of the parameters accepted by the `createRenderEffect` function in SolidJS, specifying their types and purpose.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/secondary-primitives/create-render-effect.mdx#_snippet_2

LANGUAGE: APIDOC
CODE:

```
fn: (v: T) => T
  Description: The effect function to be called.
value: T
  Description: The initial value to be passed to the effect function.
```

---

TITLE: SolidJS TypeScript Declaration for Custom Directives
DESCRIPTION: Shows how to extend the SolidJS JSX namespace to register custom directives with TypeScript, providing type safety for their expected parameter types. This example registers the `model` directive.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/jsx-attributes/use.mdx#_snippet_2

LANGUAGE: TypeScript
CODE:

```
declare module "solid-js" {
	namespace JSX {
		interface Directives {
			model: [() => any, (v: any) => any]
		}
	}
}
```

---

TITLE: Declaring and using a ref attribute in SolidJS
DESCRIPTION: This example shows the primary method of using `ref` in SolidJS to access DOM elements directly within the JSX template. The `ref` attribute assigns the DOM element to a declared variable at creation time, maintaining the component's structural integrity.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/refs.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
function Component() {
	let myElement;

	return (
		<div>
			<p ref={myElement}>My Element</p>
		</div>
	)
}
```

---

TITLE: Simple SolidJS Switch Component Implementation
DESCRIPTION: This code provides a basic implementation of the `Switch` component. It iterates through its children, returning the first `Match` component whose `when` prop evaluates to a truthy value, or the `fallback` prop if no match is found.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/components/switch-and-match.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
function Switch(props) {
	let children = props.children

	if (!Array.isArray(children)) children = [children]

	for (let i = 0; i < children.length; i++) {
		const child = children[i]
		if (child.props.when) return child
	}

	return props.fallback
}
```

---

TITLE: Create Custom SolidJS Context Hook
DESCRIPTION: This snippet shows how to create a custom `useCounter` hook in SolidJS. This utility simplifies accessing context values by abstracting the `useContext` call, making components cleaner and reducing repetitive code when consuming context.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/context.mdx#_snippet_6

LANGUAGE: JSX
CODE:

```
export function useCounter() {
	return useContext(CounterContext);
}
```

---

TITLE: TypeScript definitive assignment assertion for SolidJS refs
DESCRIPTION: When using refs in SolidJS with TypeScript, a definitive assignment assertion (`!`) is required. This signals to TypeScript that the variable will be assigned by SolidJS during component rendering, even if TypeScript cannot statically confirm it, preventing potential type errors.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/refs.mdx#_snippet_3

LANGUAGE: tsx
CODE:

```
let myElement!: HTMLDivElement;
```

---

TITLE: Define Dynamic Routes with Parameters in SolidJS Router
DESCRIPTION: This snippet demonstrates how to define dynamic routes using the SolidJS Router. The `:id` syntax allows a path segment to be treated as a flexible parameter, which can then be accessed within the component using the `useParams` primitive.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/concepts/dynamic-routes.mdx#_snippet_0

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router, Route } from "@solidjs/router";

const Users = lazy(() => import("./pages/Users"));
const User = lazy(() => import("./pages/User"));
const Home = lazy(() => import("./pages/Home"));

render(
	() => (
		<Router>
			<Route path="/users" component={Users} />
			<Route path="/users/:id" component={User} />
			<Route path="/" component={Home} />
		</Router>
	),
	document.getElementById("app")
);
```

---

TITLE: SolidStart API Route Shared Handler
DESCRIPTION: Illustrates how to reuse a single handler function for multiple HTTP methods in SolidStart API routes. This approach promotes code reusability and reduces redundancy when the logic for different methods is similar.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/building-your-application/api-routes.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
async function handler() {
  // ...
}

export const GET = handler;
export const POST = handler;
// ...
```

---

TITLE: SolidJS Native MouseMove Event for Infrequent Actions
DESCRIPTION: This snippet illustrates the use of a native `on:mousemove` event listener in SolidJS. Native events are recommended for infrequent occurrences as they do not benefit from the performance improvements of event delegation and provide more predictable behavior for specific circumstances.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/event-handlers.mdx#_snippet_7

LANGUAGE: tsx
CODE:

```
<div on:mousemove={handleCustomEvent} />
```

---

TITLE: Basic Derived Signal from a Count Signal
DESCRIPTION: In the above example, the `double` function relies on the `count` signal to produce a value. When the `count` signal is changed, the `double` function will be called again to produce a new value.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/derived-values/derived-signals.mdx#_snippet_0

LANGUAGE: js
CODE:

```
const double = () => count() * 2;
```

---

TITLE: Zerops `zerops.yml` Configuration for SSR Node.js Apps
DESCRIPTION: Example `zerops.yml` file for Server-Side Rendering (SSR) Solid.js applications. This configuration instructs Zerops on how to build and run the Node.js application, including installation of dependencies, build commands, files to deploy, and the start command for the server.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/deployment-options/zerops.mdx#_snippet_2

LANGUAGE: yaml
CODE:

```
zerops:
  - setup: app
    build:
      base: nodejs@latest
      buildCommands:
        - pnpm i
        - pnpm build
      deployFiles:
        - .output
        - node_modules
        - public
        - package.json
    run:
      base: nodejs@latest
      ports:
        - port: 3000
          httpSupport: true
      start: pnpm start
```

---

TITLE: SolidJS Dynamic Event Handlers with Reactive Sources
DESCRIPTION: Explains that while event handlers themselves are not reactive, they can be designed to call reactive sources. This example shows how a prop `handleClick` can be invoked, allowing the underlying function to be dynamic without the resource-intensive task of attaching and detaching listeners.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/event-handlers.mdx#_snippet_4

LANGUAGE: tsx
CODE:

```
<div onClick={() => props.handleClick?.()} />
```

---

TITLE: SolidJS Signal Tracking: Tracked vs. Untracked Access
DESCRIPTION: This example illustrates the difference between tracked and untracked signal access in SolidJS. Accessing `count()` outside the return statement (e.g., in `console.log`) is untracked and runs only once. In contrast, `createEffect` and JSX expressions within the return statement are tracked and react to signal changes.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/intro-to-reactivity.mdx#_snippet_7

LANGUAGE: jsx
CODE:

```
function Counter() {
	const [count, setCount] = createSignal(0);
	const increment = () => setCount((prev) => prev + 1);

	console.log("Count:", count()); // ❌ not tracked - only runs once during initialization.

	createEffect(() => {
		console.log(count()); // ✅ will update whenever `count()` changes.
	});

	return (
		<div>
			<span>Count: {count()}</span>{/* ✅ will update whenever `count()` changes. */}
			<button type="button" onClick={increment}>
				Increment
			</button>
		</div>
	);
}
```

---

TITLE: Passing Props to a Child Component in SolidJS
DESCRIPTION: Demonstrates how to pass read-only properties from a parent component to a child component using JSX attributes in SolidJS.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/props.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
function App() {
	// Passing a prop named "name" to the MyComponent component
	return (
		<div>
			<MyComponent name="Ryan Carniato" />
		</div>
	);
}
```

---

TITLE: Shallow Merge Objects with setStore in SolidJS
DESCRIPTION: Explains that when a new value is an object, `setStore` performs a shallow merge with the existing object. This means you can directly provide the new properties without manually spreading the existing object, simplifying updates.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_14

LANGUAGE: jsx
CODE:

```
setStore("users", 0, {
	id: 109,
})

// is equivalent to

setStore("users", 0, (user) => ({
	...user,
	id: 109,
}))
```

---

TITLE: SolidStart Middleware: Accessing and Modifying event.locals
DESCRIPTION: This snippet demonstrates how to use `createMiddleware` in SolidStart to access and modify the `event.locals` object. It shows how to store user data and a helper function, making them available for the current request.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/advanced/middleware.mdx#_snippet_3

LANGUAGE: ts
CODE:

```
import { createMiddleware } from "@solidjs/start/middleware";

export default createMiddleware({
	onRequest: (event) => {
		event.locals.user = {
			name: "John Wick",
		};
		event.locals.sayHello = () => {
			return "Hello, " + event.locals.user.name;
		};
	},
});
```

---

TITLE: Direct Event Listener Attachment with on:_
DESCRIPTION: Demonstrates the basic usage of `on:_`to directly attach an event handler to a DOM element using`addEventListener`. This is useful for events with capital letters or when delegation via the document is not desired.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/jsx-attributes/on.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
<div on:DOMContentLoaded={(e) => console.log("Welcome!")} />
```

---

TITLE: Set Multiple Array Elements or Object Properties by Index/Key in SolidJS
DESCRIPTION: Demonstrates how to use an array of indices or object keys with `setStore` to update a property on multiple elements or properties simultaneously. This method is more efficient than making individual `setStore` calls for each update, as it leverages Solid's batching mechanism.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_9

LANGUAGE: jsx
CODE:

```
setStore("users", [2, 7, 10], "loggedIn", false)
// equivalent to (but more efficient than):
setStore("users", 2, "loggedIn", false)
setStore("users", 7, "loggedIn", false)
setStore("users", 10, "loggedIn", false)

setStore("users", ["me", "you"], "loggedIn", false)
// equivalent to (but more efficient than):
setStore("users", ["me"], "loggedIn", false)
setStore("users", ["you"], "loggedIn", false)
```

---

TITLE: SolidJS Dynamic Component Usage Example
DESCRIPTION: Illustrates a basic usage of the SolidJS `Dynamic` component, showing how to pass a component and additional props.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/components/dynamic.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
<Dynamic component={MyComponent} someProp={state.something} />
```

---

TITLE: SolidJS Show Component with Keyed Option for Narrowing
DESCRIPTION: Demonstrates using the 'keyed' option with SolidJS's <Show> component. This approach provides a non-nullish accessor to the 'when' value, preventing child recreation on value changes while enabling type narrowing.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/configuration/typescript.mdx#_snippet_34

LANGUAGE: tsx
CODE:

```
return (
	<div>
		<Show keyed when={user()}>
			{(nonNullishUser) => nonNullishUser.name}
		</Show>
	</div>
);
```

---

TITLE: Less Optimized Selection State Without createSelector
DESCRIPTION: Presents an alternative, less optimized method for managing selection states in SolidJS. This approach directly compares `selectedId()` with `item.id` within the `For` loop, leading to more frequent and potentially unnecessary DOM updates for every list item when `selectedId` changes.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/secondary-primitives/create-selector.mdx#_snippet_2

LANGUAGE: TSX
CODE:

```
const [selectedId, setSelectedId] = createSignal()

<For each={list()}>
	{(item) => <li classList={{ active: selectedId() === item.id }}>{item.name}</li>}
</For>
```

---

TITLE: SolidJS Counter Component with createSignal
DESCRIPTION: Demonstrates a basic counter component in SolidJS using `createSignal` for state management. It shows how to initialize state, define an action to update it, and render the state in the UI.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/state-management.mdx#_snippet_0

LANGUAGE: jsx
CODE:

```
import { createSignal } from "solid-js";

function Counter() {
	const [count, setCount] = createSignal(0);

	const increment = () => {
		setCount((prev) => prev + 1);
	};

	return (
		<>
			<div>Current count: {count()}</div>
			<button onClick={increment}>Increment</button>
		</>
	);
}
```

---

TITLE: Utilize Custom SolidJS Context Provider
DESCRIPTION: This example illustrates how to use the previously defined `CounterProvider` component to wrap a component tree. By importing and using this custom provider, developers can easily apply context to different parts of their SolidJS application, promoting reusability and cleaner component structures.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/context.mdx#_snippet_5

LANGUAGE: JSX
CODE:

```
import { CounterProvider } from "./counterProvider";

export function App() {
	return (
		<CounterProvider count={1}>
			<h1>Welcome to Counter</h1>
			<NestedComponents />
		</CounterProvider>
	);
}
```

---

TITLE: Extract Raw Data from SolidJS Stores with `unwrap`
DESCRIPTION: The `unwrap` utility transforms a SolidJS store into a standard JavaScript object, providing a non-reactive snapshot of the current state. This is useful for situations requiring an unaltered view of data or when interfacing with third-party libraries that expect regular JavaScript objects.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/stores.mdx#_snippet_17

LANGUAGE: jsx
CODE:

```
import { createStore, unwrap } from "solid-js/store"

const [data, setData] = createStore({
	animals: ["cat", "dog", "bird", "gorilla"]
})

const rawData = unwrap(data)
```

---

TITLE: SolidJS Server Action Redirect After Mutation
DESCRIPTION: This TypeScript example shows how to use `redirect` within a SolidJS server action. After a user is successfully added via `postUser()`, `redirect('/users')` is returned, which navigates the user to the `/users` route and automatically sends updated data for the destination, avoiding an additional roundtrip.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/reference/response-helpers/redirect.mdx#_snippet_1

LANGUAGE: ts
CODE:

```
import { action, redirect } from "@solidjs/router";

const addUser = action(async (user: User) => {
  await postUser(user);

  return redirect("/users");
});
```

---

TITLE: Basic Usage of SolidJS Base Component
DESCRIPTION: Demonstrates importing and using the `Base` component to set a base URL and target for relative links in a SolidJS application.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-meta/reference/meta/base.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
import { Base } from "@solidjs/meta";

<Base target="_blank" href="https://docs.solidjs.com/" />;
```

---

TITLE: Returning JSON with a Promise from a SolidStart Server Function
DESCRIPTION: This example demonstrates how to return a JSON response from a SolidStart server function using the `json` helper from `@solidjs/router`. It shows a `GET` function that returns a promise-wrapped string, along with custom headers for cache control. The `json` helper ensures the server function's return type is not impacted by the helper itself.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/advanced/return-responses.mdx#_snippet_0

LANGUAGE: tsx
CODE:

```
import { json } from "@solidjs/router";
import { GET } from "@solidjs/start";

const hello = GET(async (name: string) => {
	"use server";
	return json(
		{ hello: new Promise<string>((r) => setTimeout(() => r(name), 1000)) },
		{ headers: { "cache-control": "max-age=60" } }
	);
});
```

---

TITLE: SolidJS createMutable Store and UI Dependency
DESCRIPTION: Demonstrates how to create a mutable store using `createMutable` and how UI elements can depend on its fields. This setup shows a basic example where changes to store fields would typically trigger updates.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/store-utilities/modify-mutable.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
import { createMutable } from "solid-js/store"

const state = createMutable({
	user: {
		firstName: "John",
		lastName: "Smith",
	},
});

<h1>Hello {state.user.firstName + " " + state.user.lastName}</h1>;
```

---

TITLE: Update Session Data in SolidJS
DESCRIPTION: Illustrates how to asynchronously update the current session's data. It utilizes the `useThemeSession` helper and its `update` method, requiring a `SessionData` object as input. This function is intended for server-side execution.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/advanced/session.mdx#_snippet_3

LANGUAGE: TypeScript
CODE:

```
export async function updateThemeSession(data: SessionData) {
	"use server";
	const session = await useThemeSession();
	await session.update(data);
}
```

---

TITLE: SolidJS Native Event for Non-Delegated or Custom Events
DESCRIPTION: Illustrates the use of the `on:` prefix for attaching event listeners to elements that are not supported by Solid's synthetic event delegation, such as custom events on custom elements, ensuring the event listener is added as-is.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/event-handlers.mdx#_snippet_5

LANGUAGE: tsx
CODE:

```
<div on:customEvent={handleCustomEvent} />
```

---

TITLE: Define SolidJS Preload Function
DESCRIPTION: Illustrates the basic structure of a preload function in SolidJS, showing how it receives route parameters and location information. This function is designed to initiate data fetching or other operations before a route component renders.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/routing-and-navigation.mdx#_snippet_21

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { Route } from "@solidjs/router";

const User = lazy(() => import("./pages/users/[id].js"));

// preload function
function preloadUser({ params, location }) {
	// do preload
}
```

---

TITLE: Handling Children with `children` Helper in SolidJS
DESCRIPTION: Shows how to use the `children` helper in SolidJS to safely access `props.children`, preventing issues like repeated component creation when children are accessed multiple times.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/components/props.mdx#_snippet_5

LANGUAGE: typescript
CODE:

```
import { children } from "solid-js";

function ColoredList(props) {
	const safeChildren = children(() => props.children);

	return <>{safeChildren()}</>;
}
```

---

TITLE: SolidJS: Optimal Async Data Handling with Suspense
DESCRIPTION: This snippet demonstrates the recommended way to handle asynchronous data loading in SolidJS using the <Suspense> component. It combines the benefits of immediate DOM node creation (like optional chaining) with a fallback display (like <Show>), but defers attaching the nodes to the document until the data resolves, providing an optimal balance of performance and user experience.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/components/suspense.mdx#_snippet_5

LANGUAGE: jsx
CODE:

```
const MyComponentWithSuspense = () => {
	const [profile] = createResource(async () => {
		/* fetcher code here */
	})
	return (
		<Suspense fallback={<div>fetching user data</div>}>
			<div>{profile()?.name}</div>
			<div>{profile()?.email}</div>
		</Suspense>
	)
}
```

---

TITLE: Passing Props to Dynamic Components in SolidJS
DESCRIPTION: This SolidJS snippet demonstrates how to pass properties to a component rendered dynamically using the `<Dynamic>` component. Any props provided to `<Dynamic>` are forwarded to the underlying component, similar to standard JSX prop passing.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/control-flow/dynamic.mdx#_snippet_2

LANGUAGE: jsx
CODE:

```
import { Dynamic } from "solid-js/web"

function App() {
	return (
		<Dynamic component={someComponent} someProp="someValue" />
	)
}
```

---

TITLE: Implement Lazy Loading for Config-Based Routes in Solid Router
DESCRIPTION: This snippet highlights the best practice of using the `lazy` component from Solid.js to asynchronously load components within config-based routing. Lazy loading improves application performance by deferring the loading of components until they are actually needed, reducing initial bundle size.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/getting-started/config.mdx#_snippet_2

LANGUAGE: jsx
CODE:

```
import { lazy } from "solid-js";
import { render } from "solid-js/web";
import { Router } from "@solidjs/router";

const routes = [
    {
        path: "/",
        component: lazy(() => import("/routes/index.js")),
    },
    {
        path: "/hello-world",
        component: () => <h1>Hello, World!</h1>
    },
    {
        path: "/about",
        component: lazy(() => import("/routes/about.js")),
    }
]


render(() => <Router>{routes}</Router>, document.getElementById("app"));
```

---

TITLE: SolidJS: createRenderEffect Immediate Execution Example
DESCRIPTION: Demonstrates the immediate execution of `createRenderEffect` during the rendering phase, contrasting its behavior with `createEffect`. It shows how initial values are logged immediately and how subsequent signal updates are batched and processed, including interaction with `queueMicrotask`.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/secondary-primitives/create-render-effect.mdx#_snippet_1

LANGUAGE: ts
CODE:

```
// assume this code is in a component function, so is part of a rendering phase
const [count, setCount] = createSignal(0)

// this effect prints count at the beginning and when it changes
createRenderEffect(() => console.log("count =", count()))
// render effect runs immediately, printing `count = 0`
console.log("hello")
setCount(1) // effect won't run yet
setCount(2) // effect won't run yet

queueMicrotask(() => {
	// now `count = 2` will print
	console.log("microtask")
	setCount(3) // immediately prints `count = 3`
	console.log("goodbye")
})

// --- overall output: ---
// count = 0   [this is the only added line compared to createEffect]
// hello
// count = 2
// microtask
// count = 3
// goodbye
```

---

TITLE: SolidJS: Delegating Events with Array Binding
DESCRIPTION: Illustrates how to pass a two-element array to an event handler in SolidJS to bind a value (e.g., `item.id`) to the first argument of the handler function. This method is highly optimized for event delegation as it avoids `bind` or additional closures.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/jsx-attributes/on_.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
function handler(itemId, e) {
	/*...*/
}

<ul>
	<For each={state.list}>{(item) => <li onClick={[handler, item.id]} />}</For>
</ul>;
```

---

TITLE: SolidJS Index Component for Dynamic Inputs and Signals
DESCRIPTION: The <Index> component is ideal for SolidJS applications involving signals, JavaScript primitives (strings, numbers), or input fields where individual item values might change. Unlike <For>, <Index> updates only the content at the specified index, preventing unnecessary re-renders of the entire list when values are modified, thus improving performance for dynamic data.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/control-flow/list-rendering.mdx#_snippet_5

LANGUAGE: jsx
CODE:

```
import { createSignal, Index } from "solid-js"

function FormList() {
	const [inputs, setInputs] = createSignal(['input1','input2','input3'])
	return(
		<form>
			<Index each={inputs()}>
				{(input, index) => (
					<input
						type="text"
						value={input()}
						onInput={(e) => {
							// update the input value
						}}
					/>
				)}
			</Index>
		</form>
	)
}
```

---

TITLE: Clear Session Data in SolidJS
DESCRIPTION: Shows how to asynchronously clear the current session's data. It leverages the `useThemeSession` helper and its `clear` method. This function is designated for server-side execution.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-start/advanced/session.mdx#_snippet_4

LANGUAGE: TypeScript
CODE:

```
export async function clearThemeSession() {
	"use server";
	const session = await useThemeSession();
	await session.clear();
}
```

---

TITLE: Implement Memory Mode Routing in SolidJS
DESCRIPTION: This snippet illustrates how to use MemoryRouter in SolidJS. Memory mode keeps the router's history in memory, independent of the browser's URL, which is particularly useful for testing scenarios. Replace the `Router` component with `MemoryRouter` in your application's render function.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/solid-router/concepts/alternative-routers.mdx#_snippet_1

LANGUAGE: jsx
CODE:

```
import { render } from "solid-js/web";
import {
    MemoryRouter,
    Route
    } from "@solidjs/router";

const App = (props) => (
    <>
        <h1>Root header</h1>
        {props.children}
    </>
);

render(
    () => <MemoryRouter root={App}>{/*... routes */}</MemoryRouter>,
    document.getElementById("app")
);
```

---

TITLE: Install Tailwind CSS Development Dependencies
DESCRIPTION: Installs Tailwind CSS, @tailwindcss/postcss, and postcss as development dependencies using a package manager, essential for setting up Tailwind in your project.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/styling-components/tailwind.mdx#_snippet_0

LANGUAGE: Shell
CODE:

```
tailwindcss @tailwindcss/postcss postcss
```

---

TITLE: Zerops Project Import YAML for Static Apps
DESCRIPTION: YAML configuration used for creating a Zerops project with a static service directly from the web interface's project import feature. This snippet defines the project name and a static service with subdomain access enabled.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/deployment-options/zerops.mdx#_snippet_0

LANGUAGE: yaml
CODE:

```
project:
  name: recipe-solidjs

services:
  - hostname: app
    type: static
    enableSubdomainAccess: true
```

---

TITLE: SolidJS Store: Reconcile Usage with Observable
DESCRIPTION: Demonstrates how to use `reconcile` within a SolidJS component to update a store's state (`todos`) when subscribing to an observable. It also shows cleanup using `onCleanup`.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/store-utilities/reconcile.mdx#_snippet_1

LANGUAGE: ts
CODE:

```
// subscribing to an observable
const unsubscribe = store.subscribe(({ todos }) => (
  setState('todos', reconcile(todos));
);
onCleanup(() => unsubscribe());
```

---

TITLE: Access Dynamic Route Parameters using useParams in SolidJS
DESCRIPTION: This code demonstrates how to retrieve dynamic route parameters within a SolidJS component using the `useParams` primitive from `@solidjs/router`. It shows how to access specific parameters, such as `params.id`, to display dynamic content based on the URL.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/guides/routing-and-navigation.mdx#_snippet_9

LANGUAGE: jsx
CODE:

```
import { useParams } from "@solidjs/router";

const User = () => {
	const params = useParams(); // Retrieve the dynamic route parameters
	// Now you can access the id parameter as params.id

	return (
		<p>
			This is the user with the id of <code>{params.id}</code>
		</p>
	);
};
```

---

TITLE: Utilize Custom SolidJS Context Hook
DESCRIPTION: This example demonstrates how to use the custom `useCounter` hook within a SolidJS component. By importing and calling `useCounter()`, components can directly access context values without needing to explicitly pass the context object to `useContext`, improving code readability and maintainability.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/concepts/context.mdx#_snippet_7

LANGUAGE: JSX
CODE:

```
import { useCounter } from "./counter";

export function CounterProvider(props) {
	const count = useCounter();
	return (
		<>
			<div>{count()}</div>
		</>
	);
}
```

---

TITLE: SolidJS onMount Example with Element Ref
DESCRIPTION: This example demonstrates how to use `onMount` in SolidJS to access and manipulate a DOM element after it has been mounted. It shows disabling a button using a `ref` once the component is rendered, ensuring the DOM element is available.
SOURCE: https://github.com/solidjs/solid-docs/blob/main/src/routes/reference/lifecycle/on-mount.mdx#_snippet_1

LANGUAGE: tsx
CODE:

```
// example that shows how to use onMount to get a reference to an element
import { onMount } from "solid-js"

function MyComponent() {
	let ref: HTMLButtonElement

	// when the component is mounted, the button will be disabled
	onMount(() => {
		ref.disabled = true
	})
	return <button ref={ref}>Focus me!</button>
}
```
