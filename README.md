# Reproduction for [denoland/deno#26412](https://github.com/denoland/deno/issues/26412)

## Works:
```shell
deno run main.ts
```

## Doesn't work:
```shell
deno install --global --name repro-global-package --config deno.json main.ts
```
Running the above command results in:
```text
error: Relative import path "@std/log" not prefixed with / or ./ or ../
  hint: If you want to use a JSR or npm package, try running `deno add jsr:@std/log` or `deno add npm:@std/log`
    at file:///home/anner/code/repro-deno-global-install-package-json/main.ts:1:22
```

## Also doesn't work:

```shell
deno install --global --node-modules-dir=auto --name repro-global-package --config deno.json main.ts
```
Above command succeeds, but running `repro-global-package` afterwards results in the same error as above
