you will need: 


1. 
```
yarn add graphql 
yarn add -D @graphql-codegen/cli
```

2. 
`codegen.yml` files at root (./) with
```
overwrite: true
schema: "./data/schema.graphql"
generates:
  data/generated.ts:
    plugins:
      - typescript
      - typescript-resolvers

```


Graphql schema file  at `./data/schema.graphql`
```
insert schema here
```

