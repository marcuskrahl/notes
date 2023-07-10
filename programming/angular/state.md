# State

## Best practices

- Immutable state
- Unidirectional data flow

## Types of State

- Router State / Urls
    - URL parameters which stay the same even after refresh
- Component State 
    - State belonging to a single component or a small component tree
- Persisted State
    - State which should stay fixed during a session, e.g. keep an accordion collapsed even after navigating to a different page in a SPA
- Shared State
    - State which is used in multiple places in the app, e.g. user settings

## Options

- State management libraries
	- Ngrx
	- Ngxs
	- Akita
	- rx-angular 
		- lightweight and heavily based on rxjs
- "Homebrew" variant with RxJS and singleton services
