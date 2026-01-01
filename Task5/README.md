# Проектирование GraphQL API

## Схема GraphQL

```
type Client {
  id: ID!
  name: String
  age: Int
  documents: [Document!]!
  relatives: [Relative!]!
}

type Document {
  id: ID!
  type: String
  number: String
  issueDate: String
  expiryDate: String
}

type Relative {
  id: ID!
  relationType: String
  name: String
  age: Int
}

input ClientFilter {
  id: ID
}


# Главный тип для GraphQL-запросов
type Query {
  client(id: ID!): Client
  clients(filter: ClientFilter): [Client!]!
}
```

## Примеры GraphQL-запросов для сервиса client-info:

1. Получить только основную информацию о клиенте:
```graphql
query {
  client(id: "123") {
    id
    name
    age
  }
}
```

2. Получить клиента с документами:
```graphql
query {
  client(id: "123") {
    id
    name
    documents {
      type
      number
    }
  }
}
```

3. Получить клиента с родственниками:
```graphql
query {
  client(id: "123") {
    id
    name
    age
    relatives {
      name
      relationType
      age
    }
  }
}
```

4. Получить клиента со всеми связанными данными:
```graphql
query {
  client(id: "123") {
    id
    name
    age
    documents {
      type
      number
      issueDate
      expiryDate
    }
    relatives {
      name
      relationType
      age
    }
  }
}
```

5. Получить только даты и номера документов:
```graphql
query {
  client(id: "123") {
    documents {
      number
      issueDate
      expiryDate
    }
  }
}
```
