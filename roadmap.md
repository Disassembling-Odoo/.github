# 拆解Odoo的路线图

因现阶段只有作者一人在做这件事，所以时间不能很好的保证只能说现阶段还处于1.0版本中。之后有更多的人加入时会有更好的时间表。

- 3.0版本

  - 目标：
主要目标是形成模块的独立演进能力。
  - 方式：
检查所有的模块的导入过程，以及隐式导入过程是否涉及到其他层面中的模块。如果涉及到则都贵在模块内部某一特定区域进行划分。

- 2.0版本

  - 目标：
主要目标是构建每层的可扩展性。
  - 方式：
在划分好的模块中，进行重构。并通过测试。

- 1.0版本（现阶段）

  - 目标：
主要目标是厘清边界，形成独立实体。
  - 方式：
按照模块划分将模块的功能整理完成，并通过测试。
