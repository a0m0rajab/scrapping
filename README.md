# Automation
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
#### Recoded: 

A code specific to get recoded related repos into a list

```javascript
repoCount = document.querySelector("#user-repositories-list > ul").childElementCount
information = []
for (let i = 1; i <= repoCount; i++) {
    let forked = document.querySelector(`#user-repositories-list > ul > li:nth-child(${i}) > div.col-10.col-lg-9.d-inline-block > div.d-inline-block.mb-1 > span > a`)
    if (forked) {
        let name = forked.innerText.split("/")[1].split("-")
        name.splice(-3, 3)
        information.push({ link: forked.href, name: name.join(" ") })
    }
}
let table = ""
information.forEach(e => {
    table += `[${e.name}](${e.link})\n`
})
```

### Remove Repo: 

```Javascript
document.querySelector("#js-repo-pjax-container > div.color-bg-secondary.pt-3.hide-full-screen.mb-5 > nav > ul > li:nth-child(7) > a > span:nth-child(2)").click()
let removeButton = document.querySelector("#options_bucket > div.Box.Box--danger > ul > li:nth-child(4) > details > summary")
removeButton.click()
let neededText = document.querySelector("#options_bucket > div.Box.Box--danger > ul > li:nth-child(4) > details > details-dialog > div.Box-body.overflow-auto > p:nth-child(2) > strong")
document.querySelector("#options_bucket > div.Box.Box--danger > ul > li:nth-child(4) > details > details-dialog > div.Box-body.overflow-auto > form > p > input").value = neededText.innerText
submitButton = document.querySelector("#options_bucket > div.Box.Box--danger > ul > li:nth-child(4) > details > details-dialog > div.Box-body.overflow-auto > form > button")
submitButton.disabled=false;
submitButton.click()
```
