# Svelte/`rollup_bundle` bug PoC

```
bazel build //:bundle_prod
```

This works, because the `bundle_prod` rule in `rules_svelte` has `--nobazel_node_patches` [set on `rollup_bin`](https://github.com/thelgevold/rules_svelte/blob/e2fad87744471fd202cfacba0fca2a145b22ae1e/internal/BUILD.bazel#L31-L33).

```
bazel build //:rollup_bundle
```

Fails with:

```
main.js → bazel-out/k8-fastbuild/bin/rollup_bundle.js...
[!] Error: Could not resolve './App.svelte' from main.js
Error: Could not resolve './App.svelte' from main.js
    at error (/home/jonathan/.cache/bazel/_bazel_jonathan/b2d5fa329d4598c09257baa6c707801a/sandbox/processwrapper-sandbox/7/execroot/poc/node_modules/rollup/dist/shared/rollup.js:5206:30)
    at ModuleLoader.handleResolveId (/home/jonathan/.cache/bazel/_bazel_jonathan/b2d5fa329d4598c09257baa6c707801a/sandbox/processwrapper-sandbox/7/execroot/poc/node_modules/rollup/dist/shared/rollup.js:18219:24)
    at /home/jonathan/.cache/bazel/_bazel_jonathan/b2d5fa329d4598c09257baa6c707801a/sandbox/processwrapper-sandbox/7/execroot/poc/node_modules/rollup/dist/shared/rollup.js:18211:22
    at async Promise.all (index 0)
    at async ModuleLoader.fetchStaticDependencies (/home/jonathan/.cache/bazel/_bazel_jonathan/b2d5fa329d4598c09257baa6c707801a/sandbox/processwrapper-sandbox/7/execroot/poc/node_modules/rollup/dist/shared/rollup.js:18209:34)
    at async Promise.all (index 0)
    at async ModuleLoader.fetchModule (/home/jonathan/.cache/bazel/_bazel_jonathan/b2d5fa329d4598c09257baa6c707801a/sandbox/processwrapper-sandbox/7/execroot/poc/node_modules/rollup/dist/shared/rollup.js:18186:9)
    at async Promise.all (index 0)

Target //:rollup_bundle failed to build
```
