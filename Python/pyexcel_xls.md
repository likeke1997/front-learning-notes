# 使用

```python
# 导入
import pyexcel_xls
from collections import OrderedDict
# 读取
data_get = pyexcel_xls.get_data(path)[sheet]
# 存储
data_save = OrderedDict()
datas = […] # 二维数组
data_save.update({sheet: datas})
pyexcel_xls.save_data(path, data_save)	
```