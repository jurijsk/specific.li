This page documents deploymnet of Graph SQL Server to Azure as Azure Functions (Serversless)

You will need VS code and PowerShell, this all is ment for windows users.

Steps:

(Follow https://dev.to/azure/graphql-on-azure-part-3-serverless-with-javascript-5gb9 with uses Apollo GraphQL and [this tooling](https://www.apollographql.com/docs/apollo-server/deployment/azure-functions/))
1. [Install Azure Functions extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)
2. [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Ccsharp%2Cbash&WT.mc_id=techcommunity-blog-aapowell#v2)
3. This will allow you to run:
change `project.functions` and `data-endpoint` to something of your choosing. `data-endpoint` will be request url (_example.com/api/data-endpoint_)
```
func init project.functions --worker-runtime node --language typescript
cd project.functions
func new --template "Http Trigger" --name data-endpoint
npm install --save apollo-server-azure-functions graphql
npm install
code .
```
_create the project directory, open the directory, adds the trigger, installs required packages, opens vs code_


4. copy this to `data\index.ts`:
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
5. open 'data\function.json' and change `"name": "res"` to `"name": "$return"` somewhere towards the end of the file. 
6. run `start:host` in the terminal
7. open the link from the terminal, should be http://localhost:7071/api/data
8. in the open tab copy this to the query window:
```
{
  hello
}
```

and hit play. This is the beginning.
