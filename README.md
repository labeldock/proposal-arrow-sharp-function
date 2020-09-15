# proposal-arrow-sharp-function

<table>
<thead>
<tr>
<th>With arrow sharp function</th>
<th>Stage</th>
</tr>
</thead>
<tbody>
<tr>
<td>
```js
arrayList.map(=>>Number(#))
arrayList.map(=>>new Array([#]))
```
</td>
<td>
```js
arrayList.map((value)=>Number(value))
arrayList.map((value)=>new Array([value]))
```
</td>
</tr>
<tr>
<td>
```js
arrayList.filter(=>>typeof # === 'string')
arrayList.filter(=>>typeof # |> /string|number/.test) # with proposal-pipeline-operator F-Sharp Style 
```
</td>
<td>
```js
arrayList.filter((value)=>typeof value === 'string')
arrayList.filter((value)=>/string|number/.test(typeof value))
```
</td>
</tr>
</tr>
<tr>
<td>
flow
```js
arrayList.map(:string:number=>>Number(#))
arrayList.map(:string=>>Number(#))
arrayList.map(::number=>>Number(#))
arrayList.map(:void:void=>>Number(#))
```
</td>
<td>
```js
arrayList.map((value:string):number=>>Number(#))
arrayList.map((value:string):any:number=>>Number(#))
arrayList.map((value:any):number=>>Number(#))
arrayList.map((value:void):void=>>Number(#))
```
</td>
</tr>
<tr>
<td>
with proposal-pipeline-operator F-Sharp Style 
```js
$.ajax({}) 
  |> await 
  |> =>>#.filter(Boolean)
  |> =>>#.map(=>>($(`<li>${#.label}</li>`))
  |> =>>#.map(=>>#[0])
  |> =>>#.forEach(=>>document.body.appendChild(#))
```
</td>
<td>
```js
(async ()=>{
  return (await $.ajax({}))
  .filter(Boolean)
  .map((value)=>$(`<li>${value.label}</li>`)
  .map((value)=>value[0])
  .forEach((value)=>document.body.appendChild(value))
})()
```
</td>
</tr>
</tbody>
</table>



