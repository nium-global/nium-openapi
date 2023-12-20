# nium-OpenAPI

Nium uses the `OpenAPI 3.0.*` specification to power our [API Reference.](https://docs.nium.com/apis/reference) 

## Using the OpenAPI generator

You can find examples on the official [OpenApiGenerator docs](https://github.com/OpenAPITools/openapi-generator#3---usage).

### Generating Nium supported client libraries
#### nium-python
OpenAPI Generator version: 6.1

```bash
openapi-generator-cli generate -g python \
-i nium.yaml \
-o build/generated-python \
-p packageName=nium \
--global-property apiTests=false,modelTests=false \
```