 
The user directive requires privileged access in OpenShift. Add the following security context constraint to your pod's service account. Example below is for default service account:

Raw
# oc adm policy add-scc-to-user privileged system:serviceaccount:default:default
# oc adm policy add-scc-to-group anyuid system:authenticated

# oc new-app -f demo_service.json

