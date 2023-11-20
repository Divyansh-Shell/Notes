

1. Graphql: Querry Language for APIs and a runtime for fulfilling those queries with your existing data 
2. GraphQL allows the developer to send a single query to the server that describes the exact data requirement.
3. Client has full control over which fields to fetch from the server and the databases 
4. 

```
npm install --save apollo-boost react-apollo graphql-tag graphql
```

#Apollo_Server_Playground 

	Two Main Elements: Server Holding the data and Frontend query making the request 

Shape of the request and response structure 

QUERY:                                RESPONSE:
{                                     {
  coffee {                              "coffee": {
    blend                                 "blend": "rich"
  }                                     }
}                                     }



```
QUERY:                                RESPONSE:
{                                     {
  coffee {                              "coffee": {
    beans {                               "beans": [
        blend                               {
    }                                         blend: "rich"
  }                                         },
}                                           {
                                              blend: "smooth"
                                            }
                                          ]
                                        }
                                      }
```

```
Here you can see we are simply requesting the `beans` object, with only the field `blend` being returned from that object. Each object in the `beans` array may very well contain other data other than `blend`, but GraphQL queries help us request only the data we need, cutting out any extra information that’s not necessary for our application
```

For more specific querry for reuqesting the data requests is the ability to pass arguments in your querry 


```
QUERY:                                RESPONSE:
{                                     {
  coffee(companyId: "2") {              "coffee": {
    beans {                               "beans": [
        blend                               {
    }                                         blend: "rich"
  }                                         },
}                                           {
                                              blend: "smooth"
                                            }
                                          ]
                                        }
                                      }
```

```
QUERY:                                    RESPONSE:
{                                         {
  company1: coffee(companyId: "1") {        "company1": {
    beans {                                   "beans": [
      blend                                     {
    }                                             "blend": "rich"
  }                                             }
  company2: coffee(companyId: "2") {          ]
    beans {                                 },
      blend                                 "company2": {
    }                                         "beans": [
  }                                             {
}                                                 "blend": "fruity"
                                                }
                                              ]
                                            }
                                          }
```

Variables: Replaces the static value in the querry with $VariableName 
Declare $VariableName as one of the variable accepted by the querry 
Pass VariableName: Value in the separate transport specific variables dictionary 



```
query coffeeCompany(companyId: CompanyId) {
    coffee(companyId: companyId) {
        beans: {
            type
        }
    }
}
```


initialize the client  in app.js import the ApolloClient from apollo-boost 

```
 import ApolloClient from 'apollo-boost'

 const client = new ApolloClient({uri:```
'https://yq42lj36m9.sse.codesandbox.io/'
``` })

```

```
// ./App.js
const QUERY = gql`
{
    coffee {
        beans {
            key
            name
            price
            blend
            color
            productImage
        }
    }
}
`
```

