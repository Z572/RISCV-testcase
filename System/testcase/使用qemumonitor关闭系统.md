# 使用 QEMU Monitor 关闭系统

## 操作步骤

1. 在执行 `start_vm.sh` 的终端按 `Ctrl+A C` ，或在QEMU的图形界面按下 `Ctrl+Alt+2` 切换到 QEMU Monitor
2. 在 QEMU Monitor 执行 `system_powerdown`

## 预期结果

系统被关闭

## 实际结果

与预期不符, 测试失败

可使用 <kbd>Ctrl+A C</kbd> 切换到 QEMU Monitor.
![使用qemumonitor关闭系统-1](./img/使用qemumonitor关闭系统-1.png)

输入 `system_powerdown` 后未有反映, 系统仍然正常运行
