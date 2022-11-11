## Secret

```
apiVersion: v1
kind: Secret
metadata:
  name: superSecretVars
  namespace: default
type: Opaque
stringData:
    TEST_VAR: "VALUE"
```

## Deployment

```
containers:
  ...
  env:
    - name: EXPLICITLY_SET_VARIABLE:
      value: Hi there
    - name: VARIABLE_FROM_SECRET
      valueFrom:
        secretKeyRef:
          name: superSecretVars
          key: TEST_VAR

```                  
