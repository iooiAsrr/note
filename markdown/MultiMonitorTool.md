- 主要 - 指定您要在主监视器上执行操作。

- 显示器名称，如“名称”列中所示，例如： \\.\DISPLAY1 、 \\.\DISPLAY2 、 \\.\DISPLAY3

- 显示器编号 - 显示器名称中显示的编号。（1 代表 \\.\DISPLAY1，2 代表 \\.\DISPLAY2，依此类推...）

- 显示器 ID，如“显示器 ID”列中所示，例如：MONITOR\GSM59A4\{4d36e96e-e325-11ce-bfc1-08002be10318}\0008

- 短显示器 ID，如“短显示器 ID”列中所示，例如：GSM59A4

- 显示器的序列号，显示在“显示器序列号”列中。

  

/禁用<监视器>`MultiMonitorTool.exe /disable 1 2 3`

/启用<监视器>`MultiMonitorTool.exe /enable 3 2`

/switch <监视器>`MultiMonitorTool.exe /switch \\.\DISPLAY2 \\.\DISPLAY3`

/LoadConfig <文件名>`MultiMonitorTool.exe /LoadConfig "d:\config\**.cfg"`