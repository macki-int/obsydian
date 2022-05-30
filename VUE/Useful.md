```javascript
axios.interceptors.response.use(
    response => {
        return response
    },
    error => {
        if (!error.response) {
            console.log("Please check your internet connection.");
        }

        return Promise.reject(error)
    }
)
```

```javascript
catch(error => {
        if (!error.response) {
            // network error
            this.errorStatus = 'Error: Network Error';
        } else {
            this.errorStatus = error.response.data.message;
        }
      })
```