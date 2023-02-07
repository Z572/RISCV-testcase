# MySQL 卸载

## 摘要

命令行卸载 MySQL 并移除不必要的依赖。

## 操作步骤

1. 启动 Terminal
2. 切换到 root 账户
2. 执行 `apt remove mysql-server -y|tee ./MySQL_remove.log`
3. 执行 `apt autoremove`

![MySQL卸载](./img/MySQL卸载.png)

## 预期结果

MySQL 卸载成功。

## 其他说明
