# So you think you'd like to contribute to react-dom-stream?

Awesome. This is a quick guide to give you a sense of how to set up a build environment and contribute, if you feel like it.

## Quick guide: how do I get the build running?

You need to have node, git, & npm installed. I've only tested this with node 4.2.1.

```
git clone https://github.com/aickin/react.git
git clone https://github.com/aickin/react-dom-stream.git
cd react
git checkout streaming-render-0.14
npm install
cd ../react-dom-stream
npm install
```

You are now all set; you should have a working build.

If you want to run the test suite:
```
npm test # from the react-dom-stream directory
```

If you want to run the build after changing code:
```
npm run build # from the react-dom-stream directory
```

## Where's the `lib` directory?

The first thing you'll notice when you start poking around is that the project depends on `lib/ReactDOMServer`, but there's no lib directory checked in to the `react-dom-stream` repo. What gives?

The code for server side rendering is actually in a branch in my fork of react, over at <https://github.com/aickin/react/tree/streaming-render-0.14>. The install instructions will download that repo at `./react`. 

If you want to modify the server side rendering code, you will need to modify the code under `./react/src` and then call `npm run build`  **from the react-dom-stream directory**. That will run the react build and copy the results over to `./react-dom-stream/lib`. **Do not edit the files under lib; they will not be committed to git**.

## What code should I look at?

To get a sense for what code has been forked from React 0.14, check out [this commit](https://github.com/aickin/react/commit/d650a52e806f110ebec971e048b1dbded53cacd6); it contains most of the interesting changes from upstream.

## Testing

The tests for server-side renders are all in `./react/src/renderers/dom/server/__tests__/ReactServerAsyncRendering-test.js`, which began life as a copy of `ReactServerRendering-test.js`. If you want to add some rendering tests, that'd be awesome.

To run the tests, call `npm test` **from the react-dom-stream directory**.

## Pull Requests

I am happy to accept pull requests to either project! Please make sure that the tests pass before submitting.

I do plan to require a CLA for contributors to keep the IP rights clean, but it shouldn't be too onerous, I hope. I'll update with details as I figure them out.