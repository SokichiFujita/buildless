Buildless
---------

A small (20k) compilation of [Preact](https://preactjs.com/),
[Preact Router](https://github.com/preactjs/preact-router), and
[HTM](https://github.com/developit/htm) - along with a 
[few of my own inventions](./docs/index.md) - that
allows you to write modern web applications with little-to-no
framework, and without a compilation step.

The goal here is that you should be able to create apps whose source runs directly
in the browser - just like the olden days - but which take can take full advantage
of JavaScript features that modern browsers now ubiquitously support.

## What?

A minimal buildless app looks like this:

### `index.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Simple Buildless app</title>
    <script type="module">
      import { render, useState, html } from 'https://unpkg.com/@fordi-org/buildless';

      const ClickCounter = () => {
        const [count, setCount] = useState(0);
        const increment = () => setCount(count + 1);
        return html`
          <div>
            <button onClick=${increment}>
              Clicked ${count} times
            </button>
          </div>
        `;
      };

      render(html`<${ClickCounter}/>`, document.body);
    </script>
  </head>
  <body></body>
</html>
```

That's it.  No build required.  Just serve up that file.  If you're feeling
like that's too terse, you can throw all your code into an `index.js`, and replace
that script tag with `<script async defer type="module" src="./index.js"></script>`.

## What's the catch?

Browser support.  Buildless relies on
[ES Modules support](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
in your browser, which means that, for example, IE users are lost (though Edge
users will work).

## So... documentation?

Everything in
[`preact`](https://preactjs.com/guide/v10/api-reference),
[`preact/hooks`](https://preactjs.com/guide/v10/hooks), 
and [`preact-router`](https://github.com/preactjs/preact-router)
is exported from the one module, so they are most of your documentation, 
along with a preact-bound instance [`htm`](https://github.com/developit/htm),
and [the Buildless tools](./docs/index.md).

Go. Play. Build some neat stuff.

## But what if I want to build anyway?

\*sigh\* fine.  Go [here](production.md) for information on how to make a
production build.
