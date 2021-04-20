# GraphQL Schema Syntax Shortly

```
type TypeName {
  propName: propType
  nullableType: propType!
}
```

defines type

Scalar, predefined types, are `Int`, `Float`, `String`, `ID`.
`ID` serialized as `String`.

Proprty can be of any scalar type of any of the user-defines types.

Exclamation mark (`!`) makes the proterty nullable.

_Example:_
```
type Address {
  id: ID
  city: String
  country: String
  zipcode: String
}

type User {
  id: ID
  age: Int!
  name: String
  address: Address!
  projects: [Int]!
}
```

* note the absence of commas
* list of project can be null but list element can not me null


more here:
https://graphql.org/learn/schema/
