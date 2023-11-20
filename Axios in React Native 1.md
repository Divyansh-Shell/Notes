


When making the Requests to the API using the Axios 
```
// Passing configuration object to axios
axios({
  method: 'get',
  url: `${baseUrl}/api/users/1`,
}).then((response) => {
  console.log(response.data);
});

// Invoking the get method to perform a GET request
axios.get(`${baseUrl}/api/users/1`).then((response) => {
  console.log(response.data);
});
```


Reducers 

```
As the component Grows, so does the amount of the state logic sprinkled 

Reduce the complexity by keeping the logic in one easy-to-access place 

Move the state logic --> reducer 



```
