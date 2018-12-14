# Bookmark
从百度首页的书签中导出所有书签

```js
let items = document.getElementsByClassName('dir-item s-opacity-blank3')
let result=[]
for(let i=0;i<items.length;i++){
	let title = items[i].children[2].children[0].textContent

	let links = items[i].children[3].children
	let tmp=[]
	for(let n=0;n<links.length;n++){
		let href = links[n].children[0].href
		let title = links[n].children[0].title
		tmp[n]={title,href}
    }
	result[i]={title,links:tmp}
}

let str = ''
result.map((item)=>{
	str = str+`<DT><H3 FOLDED>${item.title}</H3>
<DL><p>
    `
	item.links.map((link)=>{
		let c = `<DT><A HREF="${link.href}">${link.title}</A>
`
		str=str+c
    })
	str=str+`</DL><p>
`
})
```
