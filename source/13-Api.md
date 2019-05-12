# Api

我们在实例化Api时，以元组形式，提供全局装饰器。

例：

``` python
from flask_rest_jsonapi import Api
from your_project.security import login_required

api = Api(decorators=(login_required,))
```