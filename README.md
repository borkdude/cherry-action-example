# cherry-action-example

This is an example of how to use [cherry](https://github.com/borkdude/cherry), a JS-tooling friendly CLJS compiler, to implement a Github action.

This action prints "Hello World" or "Hello" + the name of a person to greet to the log.

It was created using
[this](https://docs.github.com/en/actions/creating-actions/creating-a-javascript-action)
tutorial.

## Running locally

Edit `action.cljs`, the ClojureScript source for this action.

Run:

``` shell
npm run action
```

to run the action locally. This will produce `action.mjs` which will be run by Node.js.

## Bundle

To bundle `action.mjs` using `ncc`, run: `npm run bundle`.  This will create
the standalone JS file `dist/index.mjs`.

## Inputs

## `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

## `time`

The time we greeted you.

## Example usage

``` yaml
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - name: Hello world action step
        id: hello
        uses: borkdude/cherry-action-example@v0.1.0
        with:
          who-to-greet: 'Mona the Octocat'
      # Use the output from the `hello` step
      - name: Get the output time
        run: echo "The time was ${{ steps.hello.outputs.time }}"
```
