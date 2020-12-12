## **安装**

``` shell
pip install loguru
```

## **使用**

``` python
from loguru import logger
logger.debug("this loguru's log, it is debug.")
```

## **新建文件**

``` python
import os, sys
from loguru import logger
BASE_DIR = os.path.dirname(os.path.abspath(__file__))
sys.path.append(BASE_DIR)
app_name = BASE_DIR.split(os.sep)[-1]
logs_dir = os.path.join(BASE_DIR, 'logs')
if os.path.exists(logs_dir) is False:
	os.makedirs(logs_dir)
log_file = os.path.join(logs_dir, '{}.{}.log'.format(app_name, '{time:YYYY-MM-DD}'))
logger.add(log_file, rotation='1 days', retention='7 days',compression='zip', encoding='utf-8')
```
