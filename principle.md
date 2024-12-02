# 原则

在实现过程中的一些原则：
1. 不要把所有的package都拉平，拉平了之后会有很多问题。例如：
> from odoo.technology.db.sql import SQL
> from odoo.technology.db import SQL
> from odoo.technology import SQL
> from odoo import SQL
这四种模式都可以导入SQL的时候，就少了SQL的命名空间的概念。这样会带来，
  1. 
