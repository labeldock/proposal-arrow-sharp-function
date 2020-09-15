# proposal-arrow-sharp-function
This is the syntax that came to mind while thinking about a function style that suits the [proposal-pipeline-operator F-Sharp Style](https://github.com/tc39/proposal-pipeline-operator/wiki#proposal-1-f-sharp-style-only-with-await).
Looking for someone to help me in drafting this syntex with TC39 stage-0

<table>
<thead>
<tr>
<th>With arrow sharp function
<th>Stage
<tbody>
<tr>
<td>
  
```js
arrayList.map(=>>Number(#))
arrayList.map(=>>new Array([#]))
arrayList.map(=>>({...#}))
```

<td>

```js
arrayList.map((value)=>Number(value))
arrayList.map((value)=>new Array([value]))
arrayList.map((value)=>({...value}))
```
<tr>
<td>

iife
```js
const label = (=>>`Total: ${#} $`)(money) 
```
<td>

```js
const label = ((value)=>`Total: ${value} $`")(money)
```

<tr>
<td>

```js
arrayList.filter(=>>typeof # === 'string')
// with proposal-pipeline-operator F-Sharp Style 
arrayList.filter(=>>typeof # |> /string|number/.test) 
```
<td>

```js
arrayList.filter((value)=>typeof value === 'string')
arrayList.filter((value)=>/string|number/.test(typeof value))
```
<tr>
<td>
  
flow
```js
arrayList.map(:string:number=>>Number(#))
arrayList.map(:string=>>Number(#))
arrayList.map(::number=>>Number(#))
arrayList.map(=>>Number(#))
```
<td>
  
```js
arrayList.map((value:string):number=>>Number(#))
arrayList.map((value:string):any:number=>>Number(#))
arrayList.map((value:any):number=>>Number(#))
arrayList.map((value:any):any=>>Number(#))
```
<tr>
<td>
  
with proposal-pipeline-operator F-Sharp Style 
```js
$.ajax({}) 
  |> await 
  |> =>>#.filter(Boolean)
  |> =>>#.map(=>>$(`<li>${#.label}</li>`))
  |> =>>#.map(=>>#[0])
  |> =>>#.forEach(=>>document.body.appendChild(#))
```
<td>
  
with proposal-pipeline-operator F-Sharp Style 
```js
$.ajax({})
  |> await 
  |> ((data)=>data.filter(Boolean))
  |> ((data)=>data.map((value)=>$(`<li>${value.label}</li>`)
  |> ((data)=>data.map((value)=>value[0])
  |> ((data)=>data.forEach((value)=>document.body.appendChild(value))
```

stage
```
(async ()=>{
  return (await $.ajax({}))
  .filter(Boolean)
  .map((value)=>$(`<li>${value.label}</li>`)
  .map((value)=>value[0])
  .forEach((value)=>document.body.appendChild(value))
})()
```
<tr>
<td>
  
with do-expressions
```js
arrayList.map(=>>do {
  if(Boolean(#)){
    #
  } else {
    0
  }
})
```

<td>

```js
arrayList.map((value)=>do {
  if(Boolean(value)){
    value
  } else {
    0
  }
})
```

</table>
