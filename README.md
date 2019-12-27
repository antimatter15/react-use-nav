# React `useNav` Hook

This is a really simple, obvious routing system for React apps. It's similar to
[react-use-path](https://github.com/zhangkaiyulw/react-use-path).

You simply call the `useNav` hook in order to get an object that can be used for routing. It
contains a few methods and properties that you'd expect, like `path`, `fullpath`, `hash`, `query`,
`rawquery`, `rawhash`. The `hash` and `query` properties are parsed objects, while `path`,
`fullpath`, `rawhash`, and `rawquery` are strings.

```js
function App() {
    let nav = useNav()
    if (nav.path === '/') {
        return <HomePage />
    } else if (nav.path === '/OtherPage') {
        return <OtherPage />
    } else {
        return <NotFoundPage />
    }
}
```

In addition, `nav` exposes a `match` method which can be used to route with express-style route
parameters.

```js
function App() {
    let nav = useNav()
    let m
    if ((m = nav.match('/file/:name'))) {
        return <div>{m.name}</div>
    } else {
        return <NotFoundPage />
    }
}
```

There is also a `pushNav` function which can be used to navigate.

Calling `useNav` automatically attaches a global event handler for all `<a>` tags so that all
same-origin links will be handled with `pushState`.
