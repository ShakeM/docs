# OAuth

Flask-REST-JSONAPI通过[Flask-OAuthlib](https://github.com/lepture/flask-oauthlib)包，支持OAuth功能。

例：



```python
from flask import Flask
from flask_rest_jsonapi import Api
from flask_oauthlib.provider import OAuth2Provider

app = Flask(__name__)
oauth2 = OAuth2Provider()

api = Api()
api.init_app(app)
api.oauth_manager(oauth2)
```

上述例子中，Flask-REST-JSONAPI的资源只要添加了装饰器，就会进行保护

```python
oauth2.require_oauth(<scope>)
```

指定范围模式如下：

```python
<action>_<resource_type>
```

动作包括：

- list：ResourceList的get方法
- create：ResourceList的post方法
- get：ResourceDetail的get方法
- update：ResourceDetail的get方法
- delete：ResrouceDetail的delete方法

例：

```
list_person
```

如果我们想定制权限范围，我们可以提供一个计算定制范围的函数。函数格式如下：

```python
def get_scope(resource, method):
        """Compute the name of the scope for oauth

        :param Resource resource: the resource manager
        :param str method: an http method
        :return str: the name of the scope
        """
        return 'custom_scope'
```

用例：

```python
from flask import Flask
from flask_rest_jsonapi import Api
from flask_oauthlib.provider import OAuth2Provider

app = Flask(__name__)
oauth2 = OAuth2Provider()

api = Api()
api.init_app(app)
api.oauth_manager(oauth2)
api.scope_setter(get_scope)
```

> 注：
>
> 我们能给定制的范围方法，起任意的名字。但是，我们必须设定两个必须参数：resource和method。就像上述例子一样。

如果我们需要禁用OAuth，或者为某个资源定制保护方法，我们可以给资源管理器添加如下选项：

例：

```python
from flask_rest_jsonapi import ResourceList
from your_project.extensions import oauth2

class PersonList(ResourceList):
    disable_oauth = True

    @oauth2.require_oauth('custom_scope')
    def get(*args, **kwargs):
        return 'Hello world !'
```

