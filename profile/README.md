## Odoo从入门到放弃

### 1. 价值分析

从几个角度分析Odoo现阶段能提供的价值，这里以十分制来进行评分。

#### **1. 架构设计 得分：-1**
- 陈旧的设计模式

  上个世纪发展出来的层次结构，已经经过多轮演进从展示-逻辑-存储的最初方式演进出MVC，MVP，MVVC等等多种形式。而Odoo还在使用最原始的方式，并且还有演进出了更加适合以Application的方式开发的DDD模式。

- 模块边界模糊

  逻辑边界极其混乱，在tools模块中即包括业务逻辑还包括基本的工具的能力。而且将tools中逻辑分离出来非常困难。http代码cron代码混在一起。

- 混乱的依赖关系

  在查看设计过程中，发现很多混乱的调用关系。最显著的特点就是在python脚本文件的最后看到import语句，并且有很多循环引用的场景存在。

#### **2. 技术 得分：0**

使用上世纪的技术栈进行管理与开发：
1. **服务端渲染**：未使用RESTful，GraphQL技术。
2. **大面积使用XML**：未使用Toml，Yaml技术
3. **文件存储**：未使用minio，oss技术
4. **缓存技术**：未使用Redis技术

#### **3. 可扩展 得分：0**

通过模块的方式对整体系统进行规划与设计。这是非常好的模式扩展方式，但是大家可以对比一下K8s的扩展模式。K8s的扩展模式是使用数据标准+事件+处理的方式进行的。
- 扩展的隔离性

  odoo中的扩展性是将模块加载到自己的框架下。这样就会导致，如果模块中有一些恶意代码根本就无法屏蔽。再加上odoo本身的混乱情况，如果模块中对odoo中的内容进行了错误操作都很难进行调查。
  
- 扩展的标准化

  odoo的标准化使用Model、Controller等进行标准化，未达到标准实现进行可用生命周期管理的高度。

#### **4. 业务支持能力 得分：0**

业务支撑能力：i18n，导入导出，定时任务，认证授权，短信，邮件，收付款，全文检索，BPM，Session管理，文件上传，AI等等。从这些方面来看能力是不足以达到开箱即用的程度，甚至有的还没有支持。

#### **5. 开发能力支撑 得分：0**

原先认为Odoo只需要做模型定义，展示定义。就可以完整数据库生成、API生成、基本功能生成。然后就需要实现一个稍微需要一点业务逻辑实现的代码即可。相当于Low-Code的实现方式。结果根本打不到这个水平的开发能力。

#### **6. 集成化 得分：0**

在集成度的情况下，Odoo还在解决最底层的技术问题，没有解决业务能力、开发能力支撑的角度进行支撑。所以，为了支撑集成化的能力提供的erp功能也不能形成完整的erp能力。

#### 结论：
Odoo是上个世纪的产物，但它没有跟上世界的脚步。例如：微服务化中中的前后端分离，Cache的KV数据库的使用，Session的文件存储。不过Odoo却用上了Python3这样随着时代发展而不断发展的语言。只能说Odoo的脑子认为Python3比跟随时代的思想发展更重要。




### 2. 明确的缺点
从几个方面说：
1. odoo还在使用服务端渲染的方式进行渲染，无法进行前后端分离，不利于SEO优化。
2. odoo的可扩展性大部分是基于Python的解释性语言进行的，没有提供更多的能力。
3. odoo的内部结构混乱，例如：tools中包含了过多业务内容，而不是单一职责的只有工具的代码。tools中的代码还引用了config、modules的代码。
4. odoo的sevice的代码更为混乱，将http代码cron代码混在一起。根本讲关键部分抽离出来形成一眼可以看懂的逻辑。
5. odoo有两个addons目录，一个是在odoo目录下负责基本的业务支持，一个在外部目录下负责实现业务。但外部的addons又包含了所有的i18n的语言配置。
6. 对比Java的生态系统下，odoo没有演进，一直停止在web服务刚起步的技术上。提供的基本业务支持有没有很好的适应现在的场景。


在某些原因下想将Odoo以Golang进行重新实现，研究后发现Odoo有[很多问题](https://github.com/Disassembling-Odoo/.github/blob/main/README.md)。所以，这里将原来Golang重新实现的想法变为拆解Odoo。增强其各方面能力。

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
