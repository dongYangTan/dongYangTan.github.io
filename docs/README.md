<!--
 * @Date: 2024-01-16 11:47:24
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-26 15:10:13
 * @FilePath: /dongYangTan.github.io/docs/README.md
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