# Docker Registry on OpenShift

While OpenShift does include a built-in registry, it can often be helpful to quickly spin up a standalone registry for working with other images or apps.

## Usage

### Command Line

```bash
oc project <your-project-here>
oc create -f ./registry.yaml
oc new-app --template=registry
# or to use parameters:
oc new-app --template=registry --param=REGISTRY_IMAGE="library/registry:2" --param=HOST="registry.example.com"
```

### Console

1. From the *"Add to Project"* screen, select *Import YAML/JSON* and either paste or upload the contents of the [registry.yaml](./registry.yaml) file
2. Click *Create*, then *Continue* on the popup. You can optionally save the template if you intend to deploy more.
3. Change any parameters you want and click *Create* to start the deployment.

## Notes

- The template includes a volume claim requesting 10GB of storage (by default). Please ensure there is sufficient storage available.
- Note that deploying more than one in the same project may fail due to naming conflicts.
- The registry deployment *should* be scalable, but please note this has not been tested.