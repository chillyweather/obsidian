JS Notes

```js
  _checkResponse(res) {
    if (res.ok) {
      return res.json();
    }
    return Promise.reject(`Error: ${res.status}`);
  }



  getCardList() {
    return fetch(`${this._baseUrl}cards`, {
      headers: {
        authorization: this._authToken,
      },
    })
    .then(this._checkResponse)
```