# GraphQL Schema Syntax Shortly

**TD/DR;**

* keywords: `scalar` `type` `enum`
* scalar types: `Int` `Float` `String` `ID`
* no commas
* `!` for non-nullable e.g. propName: Int!
* `[Int!]` for nullable collection of non-nullable elements



## longer version

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

Exclamation mark (`!`) makes the proterty non-nullable.

You can define scalar as follows:

```scalar Date```

User-defined scalar are serialized and persisted as default scalars at the end. 


To define enum:

```
enum EnumName {
  ConstOne,
  ConstTwo
}

```


_Example:_
```
scalar Date


enum UserType {
  basic
  pro
}

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
  projects: [Int!]
  type: UserType
  createdAt: Date
}
```

* note the absence of commas
* list of project can be null but list element can not me null




more here:
https://graphql.org/learn/schema/
