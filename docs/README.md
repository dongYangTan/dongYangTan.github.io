<!--
 * @Date: 2024-01-16 11:47:24
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-16 14:27:22
 * @FilePath: /docs/README.md
-->
# 正文标题

> An awesome project.

[操作指南>>>](./detail/detail.md)  

## 标题1
文本内容啊
 ### 标题1-1  
文本内容啊

## 标题2
古之学者必有师。  
师者，  
所以传道受业解惑也。    
人非生而知之者，  
孰能无惑？    
惑而不从师，  
其为惑也，  
终不解矣。   
生乎吾前，  
其闻道也固先乎吾，  
吾从而师之；   
生乎吾后， 
其闻道也亦先乎吾，  
吾从而师之。  
吾师道也，  
夫庸知其年之先后生于吾乎？  
是故无贵无贱，  
无长无少，  
道之所存，  
师之所存也。

## 标题3
```
const Detail = () => {

    const [param] = useSearchParams()
    const nav = useNavigate();
    const pop = () => {

        nav(-1)
    }
    return (
        <div>

            <div onClick={pop}>pop</div>
            detail{param.get('id')}

        </div>
    )
}
export default Detail
```