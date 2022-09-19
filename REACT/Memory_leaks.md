https://www.loginradius.com/blog/engineering/how-to-fix-memory-leaks-in-react/#fixes-for-memory-leaks

A memory leak is a commonly faced issue when developing React applications. It causes many problems, including:

affecting the project's performance by reducing the amount of available memory;
slowing down the application; and
crashing the system.

## Primary Causes Of Memory Leaks

React components that perform state updates and run asynchronous operations can cause memory leak issues if the state is updated after the component is unmounted. Here is a normal scenario that causes this memory leak issue:

The user performs an action that triggers an event handler to fetch data from an API.
After that, a user clicks on a link, which navigates to another page before completing step #1.
Now, the first action completes and passes the data retrieved from the API and calls function, which updates the state.
Since the component was unmounted and function is being called in a component that is no longer mounted, it causes memory leak issue -- and in the console, you'll get a warning.
