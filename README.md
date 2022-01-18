# smtp-relay-k8s
Deploy smtp relay in openshift based in a personal and official cooked image by cristiancasis.com

STEPS

```
docker build . -t registry
docker push registry
oc create ns postfix;
oc apply -f deploy.yaml
oc apply -f route.yaml
```

After this:

```
oc create sa postfix
oc adm policy add-scc-to-user anyuid -z postfix -n postfix
oc get deployment
oc edit deployment/postfix


oc edit deployment/<Deployment_Name>        OR     $ oc edit dc/<DeploymentConfig_Name>


securityContext: {}
serviceAccountName: <ServiceAccount_Name>        <------ Add ServiceAccount Name after securityContext in Deployment/DeploymentConfig and save it.

Example:

securityContext: {}
serviceAccountName: postfix                <-------
terminationMessagePath: /dev/termination-log
terminationMessagePolicy: FallbackToLogsOnError

```