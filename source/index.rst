Flask-REST-JSONAPI
==================

.. Flask-REST-JSONAPI** 是一款快速构建REST API的Flask插件。框架在遵循**JSONAPI 1.0**规范的同时，保持着极强的灵活性。框架设计之初，就考虑到了生产环境的复杂性，所以在**Flask-REST-JSONAPI**中就引入了**逻辑数据抽象层**的概念，框架中叫做**Resource(资源)**。Resource可以通过**Data layer(数据层)**接入任何ORM框架或数据库。（译者注：逻辑数据对应的是物理数据，数据库储存的是物理数据，但有时API返回的数据，不能直接返回数据库的物理数据，需要进行逻辑加工后，才能返回给用户。）

.. toctree::
   :maxdepth: 2

   01-安装.md
   02-快速上手.md
   03-逻辑数据抽象层.md
   04-资源管理器.md
   05-数据层.md
   06-路由.md
   07-过滤.md
   08-包含关联对象.md
   09-稀疏字段.md
   10-分页.md
   11-排序.md
   12-错误.md
   13-Api.md
   14-权限.md
   15-OAuth.md
   16-配置.md



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
