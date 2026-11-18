# TEMPORARY: nginx-proxy 1.11.6 ships nginx 1.31.3, which is affected by the Nov 2026
# critical CVEs (fixed in 1.31.9 / 1.30.7). Upstream tracking:
# https://github.com/nginx-proxy/nginx-proxy/issues/2791
# https://github.com/nginx-proxy/nginx-proxy/pull/2778
# Remove the nginx-patched stage once nginx-proxy publishes an image with nginx >= 1.31.9.
FROM nginx:1.31.9-alpine AS nginx-patched

FROM nginxproxy/nginx-proxy:1.11.6-alpine

# nginx binary and dynamic modules must come from the same build to stay ABI compatible
COPY --from=nginx-patched /usr/sbin/nginx /usr/sbin/nginx
COPY --from=nginx-patched /usr/lib/nginx/modules/ /usr/lib/nginx/modules/

COPY conf.d/* /etc/nginx/conf.d/
COPY nginx.tmpl /app/
