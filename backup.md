1,
从仪表板打开 DCONF 编辑器并导航到键 /ORG/GNOME/DESKTOP/INPUT-SOURCES/XKB-OPTIONS 并将其值设置为：

['TERMINATE:CTRL_ALT_BKSP', 'LV3:RALT_SWITCH']

2,

DATABASE_URL=POSTGRESQL://POSTGRES:POSTGRES@192.168.2.3:5432/PLANCK
ZSL99A@LIVE.COM 123456

3,
SUDO CLOUD-INIT QUERY -A > TARGET/CLOUD-INFO.JSON

1、

GTC: 正常挂单，如果打到对方则立即成交
GTX: 正常挂单，如果打到对面则取消, 不能为 MAKER 则取消

3,重置数据库
cargo sqlx migrate revert
cargo sqlx migrate run

4,
合约类型：永续合约，交割合约
所有合约都有正反（保证金类型）

资产类型：Spot,永续合约,Future,Option（）
钱包类型：现货账户，期货账户，统一账户，
账户类型：钱包类型的组合
市场类型：丢弃

5,
下单的时候才需要关注 SymbvolInfo 中的最小下单量的数据，只是下单接口的话值关心 symbol

1,启动 redis
sudo snap start redis

编写 rust Service: sudo vim /etc/systemd/system/rust.service
[Unit]
Description=Rust Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/ubuntu/strategies
ExecStart=/home/ubuntu/strategies/target/release/mm
Restart=always
PermissionsStartOnly=true

[Install]
WantedBy=multi-user.target

编写 bun Service: sudo vim /etc/systemd/system/metadata.service
[Unit]
Description=bun Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/ubuntu/planck
ExecStart=/home/ubuntu/planck/planck-metadata/metadata
Restart=always
PermissionsStartOnly=true

[Install]
WantedBy=multi-user.target

编译 metadata: bun build ./src/index.ts --compile --outfile=metadata

重新加载 Service 文件：sudo systemctl daemon-reload
重启 Service: sudo systemctl restart rust
查看 Service 日志：journalctl -u rust -n 100
查看 Rust 日志：tail -fn 100

linux 定时任务: crontab -e
