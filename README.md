# scrapping
A set of JS codes and some notes used to scrap data by using the browser from specific websites.

## GitHub: 

### Get repos from repo tabs

```javascript
repoCount = document.querySelector("#user-repositories-list > ul").childElementCount
information = []
for (let i = 1; i <= repoCount; i++) {
    let forked = document.querySelector(`#user-repositories-list > ul > li:nth-child(${i}) > div.col-10.col-lg-9.d-inline-block > div.d-inline-block.mb-1 > span > a`)
    information.push({ link: forked.href, name: forked.innerText })
}
```
