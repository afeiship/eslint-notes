# extends
- http://eslint.cn/docs/user-guide/configuring#extending-configuration-files

~~~
rules 属性可以做下面的任何事情以扩展（或覆盖）规则：

1. 启用额外的规则
改变继承的规则级别而不改变它的选项：
基础配置："eqeqeq": ["error", "allow-null"]
派生的配置："eqeqeq": "warn"
最后生成的配置："eqeqeq": ["warn", "allow-null"]


2. 覆盖基础配置中的规则的选项
基础配置："quotes": ["error", "single", "avoid-escape"]
派生的配置："quotes": ["error", "single"]
最后生成的配置："quotes": ["error", "single"]
~~~