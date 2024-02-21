# nginx-proxy

Repository for dockerized nginx proxy deployable on VPS

> Important
> When updating nginx-proxy, always update `nginx.tmpl` file as well. Instructions on how to do that are in "Working with nginx.tmpl" section below.

## Working with nginx.tmpl

1. Create `nginx.new.tmpl` file and copy over [`nginx.tmpl` content from `nginx-proxy` repo](https://github.com/nginx-proxy/nginx-proxy/blob/main/nginx.tmpl) into it and `nginx.tmpl` in this repo.

2. Apply changes from `nginx.tmpl.patch` into `nginx.tmpl`.

```bash
patch nginx.tmpl nginx.tmpl.patch
```

> If the command above does not work it's possible that contents of `nginx.tmpl` have changed in new version of `nginx-proxy`. In such case you'll need to apply those changes manually.

3. Make other changes you need in `nginx.tmpl` file.

4. Generate a new `.patch` file.

```bash
diff -u nginx.new.tmpl nginx.tmpl > nginx.tmpl.patch
```

5. Now you can safely remove `nginx.new.tmpl` file.
