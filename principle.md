# 原则

在实现过程中的一些原则：
1. 不要把所有的package都拉平，拉平了之后会有很多问题。例如：
```python3
from odoo.technology.db.sql import SQL # 从一个文件中导出符号
from odoo.technology.db import SQL # 从包中导出符号
from odoo.technology import SQL # 从上层包中导出符号
from odoo import SQL # 从最顶层包中导出符号
```
这四种模式都可以导入SQL的时候，这样会带来：

  - 少了SQL的命名空间的概念，会将最外层明明空间占满。
  - 少了符号的归属感，使用无法使用package的方式进行隔离。
