# Install kong
reference: https://github.com/Kong/charts

### Run:
```commandline
helm repo add gatekeeper https://open-policy-agent.github.io/gatekeeper/charts
helm repo update
helm install gatekeeper/gatekeeper --name-template=gatekeeper --namespace gatekeeper-system --create-namespace
```

### References:
- [Gate keeper Installation](https://open-policy-agent.github.io/gatekeeper/website/docs/install/)
- []()
