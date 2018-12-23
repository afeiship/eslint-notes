# eslint-prettier
+ https://blog.csdn.net/openglnewbee/article/details/79852645


## 根据出错的日志:
step1 : 根据出错的日志，比如

http://eslint.org/docs/rules/space-before-function-paren  Missing space before function parentheses  

去eslint官网搜索，找到对应的规则

 step2: 编辑eslintrc.js配置文件，在其中的rules栏目里加上一行：

'space-before-function-paren': 0,
搞定。

起因： prettier的代码自动规整的一些style风格和eslint的个别规则是冲突的，所以导致开发效率受到影响。

参考：https://github.com/prettier/prettier/issues/3847 这里有很多争论。对于注重实效的程序员来说，解决问题始终是第一重要的。

## 截图：
<img src="https://ws1.sinaimg.cn/large/006tNbRwgy1fygue41qnzj30ru0rwaee.jpg" width="500" />