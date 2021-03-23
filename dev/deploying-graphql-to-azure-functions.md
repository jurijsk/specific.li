This page documents deploymnet of Graph SQL Server to Azure as Azure Functions (Serversless)

You will need:

1. VS code
2. [Azure Functions extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)


Steps:

(Follow https://dev.to/azure/graphql-on-azure-part-3-serverless-with-javascript-5gb9 with uses Apollo GraphQL and [this tooling](https://www.apollographql.com/docs/apollo-server/deployment/azure-functions/))

1. [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Ccsharp%2Cbash&WT.mc_id=techcommunity-blog-aapowell#v2)
2. This will allow you to run:

```
func init func-project-name --worker-runtime node --language typescript
cd func-project-name
code .
```
_create the project, open the directory and open the directory in vs code._

3. create http trigger with will serve the data
```
func new --template "Http Trigger" --name data
```
--name can be anything

4. install dependencies
```
npm install --save apollo-server-azure-functions graphql
```
5. copy this to `data\index.ts`:
```
import {ApolloServer, gql} from "apollo-server-azure-functions";

const typeDefs = gql`
    type Query {
        hello: String
    }
`;

const resolvers = {
	Query: {
		hello() {
			return "Say hello to data delivered over GraphQL!";
		}
	}
};
const server = new ApolloServer({typeDefs, resolvers});
export default server.createHandler();
```
6. run `funct start` in the terminal
7. open the link from the terminal, should be http://localhost:7071/api/data
8. in the open tab copy this to the query window:
```
{
  hello
}
```

if you are using TypeScript, you need to enable esModuleInterop in your tsconfig.json file.
