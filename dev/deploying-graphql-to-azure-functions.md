# How to setup GraphQL API as Azure Functions (Loacally)

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

Adding setting to Azure Fucntion App to access via `process.env`

_**manually:**_ 
go to Function App / Settings / Configuration / Application Settings tab and do your thing.

_**sustainably:**_

1. [Install Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli)
2. run `az login` in PowerShell
3. run `az functionapp config appsettings list --n FuncAppName --g ResGroupName` so see what is already there.
4. run `az functionapp config appsettings set --n FuncAppName -g ResGroupName --settings "settingname=$settingvalue"` 
e.g.
`
az functionapp config appsettings set -n copycanecho -g Copycan --settings "hereitis=thevalue"

`
_**locally:**_
1. add or open [`local.settings.json`](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Ccsharp%2Cbash#local-settings-file) in/to the root directory of the project.
2. add key value pair to the Values collection


## Pick up here:
https://docs.microsoft.com/en-us/azure/azure-functions/functions-develop-vs-code?tabs=nodejs
https://techcommunity.microsoft.com/t5/apps-on-azure/graphql-on-azure-part-3-serverless-with-javascript/ba-p/1576922
https://azure.microsoft.com/en-us/resources/videos/build-2019-build-scalable-apis-using-graphql-and-serverless/
https://www.apollographql.com/docs/apollo-server/deployment/azure-functions/

https://blog.bitsrc.io/apollo-and-relay-side-by-side-adb5e3844935


https://react-query.tanstack.com/comparison

