

# For Openshift:
The user directive requires privileged access in OpenShift. Add the following security context constraint to your pod's service account. Example below is for default service account:
### oc adm policy add-scc-to-user privileged system:serviceaccount:default:default
### oc adm policy add-scc-to-group anyuid system:authenticated

### oc new-app -f demo_service.json

# For docker:
 docker run --rm --name openresty -p 8443:8443 \
  -v $(pwd)/nginx.conf:/usr/local/openresty/nginx/conf/nginx.conf:ro \
  -v $(pwd)/client.crt:/usr/local/openresty/nginx/conf/client.crt:ro \
  -v $(pwd)/server.crt:/usr/local/openresty/nginx/conf/server.crt:ro \
  -v $(pwd)/server.key:/usr/local/openresty/nginx/conf/server.key:ro \
  openresty/openresty:centos
