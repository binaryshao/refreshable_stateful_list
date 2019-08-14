# refreshable_stateful_list

refreshable list with views in multiple status (such as loading , empty, error) and give the chance to retry.

支持下拉刷新、上拉加载的列表，同时列表会自动切换到不同状态（比如加载中、错误、空数据）下，在错误和空数据视图中可以重试。

支持请求多个接口
只有一个接口能分页，默认为 [_requests] 中最后一个接口
刷新时，请求所有接口
上拉加载更多时，只请求分页接口

业务方可以控制很多配置，包括：

必传参数：
- 数据源列表（_requests），有三种类型的数据源：
    - Future（此时按没有分页处理）
    - 返回值为 Future 的方法（此时按分页处理，传入的方法只允许有1个参数：页码）
    - 数据列表
- 每个数据源的 tag，方便业务方区分，以实现不同业务 （tags）
- 每个数据源对应数据的 key，根据 key 获取每个接口返回的列表 （dataKeys）
- 每个 item 的构建方法 （_buildItem，该方法会收到两个参数：数据 和 索引）

可选参数：
- 是否可以下拉刷新 （refreshable，默认为 true）
- 分页时的初始页码 （initPageNo，默认为0）
- 判断是否还能分页的 key （pageCountKey，默认为 pageCount）
- 分隔线 （divider，默认为一条线）
- 是否显示悬浮按钮，返回到列表顶部 （showFloating）
- 监听事件，用于刷新列表数据 （listenTypes）
  要实现该功能，请使用 '/event' 中的 eventBus 发送事件

APIs：
- jumpTo(double value)
- animateTo(double offset, Duration duration, Curve curve)