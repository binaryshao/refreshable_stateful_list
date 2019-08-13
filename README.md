# refreshable_stateful_list

refreshable list with views in multiple status (such as loading , empty, error) and give the chance to retry.

支持下拉刷新、上拉加载的列表，同时列表会自动切换到不同状态（比如加载中、错误、空数据）下。

可以传入的数据源有三种：
- Future（此时按没有分页处理）
- 包含 Future 的方法（此时按分页处理）
- 数据列表

业务方可以控制很多配置，包括：
- 是否可以下拉刷新 （refreshable，默认为 true）
- 分页时的初始页码 （initPageNo，默认为0）
- 判断是否还能分页的 key （pageCountKey，默认为 pageCount）
- 分隔线 （divider，默认为一条线）
- 是否显示悬浮按钮，返回到列表顶部 （showFloating）
- 监听事件，用于刷新数据 （listenTypes）
