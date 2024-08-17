1， TradingStatus 采用 enum 映射

2, ticker 作为 一档 depth 接入

3, bitget futures 下单时需要指定 仓位模式，保证金币种

4, bitget 检查杠杆，持仓模式，持仓方向设置

5, 批量撤单是否支持 Vec<cid> 和 Vec<oid>

6, trader 是按照 symbol 创建的，但是 wallet_stream 是按照 auth + wallet_type 订阅更新 wallet， 也就是说 wallet 上存储的 open_orders: HashMap<Symbol, Vec<Order>>，如果要撤所有订单则需要多个 trader
有些交易所（gate）在撤所有开单或批量撤单时，需要提供 symbol 参数

首先过一下目录调整：crate 替换为 tests 集成测试
integration 的调整
cancel_all_orders 重构
gtx_place_test 重构

8, gtx 下单（buy， sell）:
无法成为挂单方就撤单: 下单返回拒绝错误 or 下单返回成功 + 订单推送 status: reject
挂单成功，需要对共有行情深度做校验，挂单增加下单量，撤单减少下单量
等待挂单成交，

9, ioc 下单（buy， sell）：
无法立即成交(吃单)的部分就撤销

10, 结算资产 和 保证金资产 一定是一样的吗 private_tester/mod.rs:check_margin_position：324

11, 不满足下单类型的订单，是直接在下单接口返回失败，还是在 wallet 时间推送拒绝 private_tester/order_gtx.rs:place_reject：118
两种情况都需测试

13, 手续费校验：
spot
买单手续费以 base 资产结算
卖单手续费以 quote 资产结算
margin private_tester/mod.rs:generic_fill_check：260
逐仓：todo
全仓位：todo
注意：base，quote，抵扣币

14,下单测试模块(buy,sell)
下单方式(gtc,gtx,ioc,fok)
共有行情（订单簿正确更新）
私有行情（资产变化，仓位变化，保证金变化）

7, 撤单测试： 需要对已经实现了 CancelMethod 的所有撤单方法进行测试

12, 部分成交的测试

15, 资费测试

16, 交割测试

18, 最小下单量是否成立 private_tester/mod.rs:post_amount
buy 为 min_base_amount
sell 为 min_quote_amount

如果 OrderAmountUnit 为 quote，则需要把 base 再转换为 quote

19,
开仓测试完成后为什么没有平仓: 需要平仓 generic_fill_check？: order_ioc:try_to_fill_ioc
如果按最小下单量测试订单，成交之后收取手续费，如果收取 base，平仓时小于最小下单量： 最小下单量需要调整（2 倍最小）
ioc_buy
20, 检查 trade 的逻辑是否也是通用的，合并到 generic_fill_check？ side 作为参数整合到 generic_fill_check private_tester/order_ioc.rs:try_to_fill_ioc:74

search_trade_with_order 需要考虑 taker/maker 成交：
taker： price,amount,side
maker: price,side

21, OrderSide 和 DepthSide 相同？ TradeSide 和 OrderSide 相反？
需要考虑是 taker or maker

22, 重构的一些方法

private_tester/mod.rs:check_place_order_base

private_tester/mod.rs:check_cancel_order_base

private_tester/mod.rs:place_amount

private_tester/mod.rs:get_last_order

private_tester/generic_tester/mod.rs:get_level

23, 逻辑是否正确

private_tester/generic_tester/mod.rs:search_trade_with_order
