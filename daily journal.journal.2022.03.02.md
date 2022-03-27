---
id: 034jntynzr8y8lot3sl9nwb
title: '2022-03-02'
desc: ''
updated: 1648322649428
created: 1646237353392
---


Some progress yesterday, especially when it comes to key bindings and overall environment setup.

- [ ] Need to spend some time getting my editor panels defined.

```
<script type="txt/javascript">
const tags= ['h5','p','li']
const words=[['eweler', 'eweller'],['ewelry','ewellery']]
const company='Jewelers Mutual'
for (let i=tags.length-1; i>=0; i--){
    for (let j=words.length-1; j>=0; j--) {
        xr = document.evaluate("//"+tags[i]+"[contains(.,'"+words[j][0]+"')]", document, null, XPathResult.ANY_TYPE, null)
        let rs=[]        
        while (r=xr.iterateNext())rs.push(r);
        for (let k=rs.length-1; k>=0; k--){
            rs[k].innerText = rs[k].innerText.replace(company,company.toUpperCase()).replace(words[j][0], words[j][1]).replace(company.toUpperCase(), company)
        }
    }
}
</script>
```


Flow Charts
graph TD; A-->B; A-->C;
Sequence Diagrams
sequenceDiagram participant Alice participant Bob Alice->>John: Hello John, how are you? John-->>Alice: Great! John->>Bob: How about you? Bob-->>John: Jolly good! 




