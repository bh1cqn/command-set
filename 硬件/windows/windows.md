
## windows环境硬件信息查询

#### 查询主板信息
``` powershell
Get-WmiObject Win32_BaseBoard | Select-Object Manufacturer, Product, Version
```

#### 查询内存频率、速度
``` powershell
Get-WmiObject Win32_PhysicalMemory | Select-Object Capacity, Speed
```

