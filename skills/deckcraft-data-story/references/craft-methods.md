# 本场景的 Craft 方法与参数

先读取输入与当前选择。数值、路径、名称和对象编号仅为格式示例；用当前输入、实际返回ID和目标尺寸替换后执行。

| 顺序与目的 | 实际方法 | 参数例子 |
| --- | --- | --- |
| 1. 先建立结论标题页 | `slide.new` | `{"layout":"titleOnly","title":"结论与数据依据"}` |
| 2. 用真实数据创建比较图 | `insert.chart` | `{"type":"column","categories":["A","B"],"series":[{"name":"指标","values":[21,42]}]}` |
| 3. 标注数据来源与限制 | `slide.notes` | `{"text":"原表、单位、时间范围、异常项与比较限制"}` |

## 如何调用

宿主内已打开编辑器时使用该同会话MCP；先等待editor_status就绪，读取实际工具schema和当前命令参数。独立CLI可用于文件任务，但新进程与已打开Web编辑器不是同一状态。

本插件MCP包装：`run_command`，参数 `{"command": "slide.new", "params": {"layout": "titleOnly", "title": "结论与数据依据"}}`。后续行保持同一会话和对象选择，逐条检查实际结果。

CLI 语法（下面是展示用写法，实际跨平台执行用argv避免shell引号差异）：

deckcraft-cli run --in input.deckcraft --cmd 'slide.new={"title":"标题"}' --save output.deckcraft。创建新文稿时省略 --in。

## 参数核对与完成标准

先查 [当前版本观察目录](craft-command-evidence.json) 中对应方法的完整参数，再按实际运行时查询更新。结构化步骤见 [craft-steps.json](craft-steps.json)。

图表比例不误导，结论与证据一致，使用同口径比较。

边界：不为视觉冲击截断轴或隐藏不利数据；图例单位必须可读。

保存可编辑工程后由新进程或重新打开的同一宿主会话核对；导出格式单独解码/查看。方法存在和零退出不代表本场景已经完成。

工作流来源与许可见 [workflow-sources.json](workflow-sources.json)。仅借鉴事实与方法，本文与参数例子原创编写。
