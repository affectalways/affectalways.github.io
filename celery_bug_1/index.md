# Celery_bug_1


## Celery：Import fails with SyntaxError: invalid syntax

按照celery官方文档进行操作时，遇到如下bug：

Import fails with `SyntaxError: invalid syntax`

```
  File "<string>", line 1, in <module>
  File "/Users/ayush/hn/vnev/lib/python3.7/site-packages/aiohttp/__init__.py", line 6, in <module>
    from .client import BaseConnector as BaseConnector
  File "/Users/ayush/hn/vnev/lib/python3.7/site-packages/aiohttp/client.py", line 3, in <module>
    import asyncio
  File "/usr/local/lib/python3.7/site-packages/asyncio/__init__.py", line 21, in <module>
    from .base_events import *
  File "/usr/local/lib/python3.7/site-packages/asyncio/base_events.py", line 296
    future = tasks.async(future, loop=self)
                       ^
SyntaxError: invalid syntax
```



**环境**：

windows 10

python3.7.4

aiohttp 3.6.1

asyncio 3.4.3



**解决**

版本不兼容，重新安装了`aiphttp`，用`aiohttp 3.6.2`版本解决了该问题


