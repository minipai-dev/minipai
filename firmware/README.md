# Motion Board Firmware

MCU（STM32 / GD32 / ESP32）实时运动层。

## 职责

低延迟状态采集、Servo Bus、时间戳，以及**安全层**：

- Watchdog
- Joint limit / Velocity limit
- Thermal shutdown
- Emergency relax
- Fall detection

安全层是一等公民，不是后补功能。

## 规范

- 遵循 MISRA C 关键规则
- 避免动态内存分配，优先静态分配
- 中断处理函数保持简短
- 硬件寄存器与中断共享变量使用 `volatile`
- 位操作用宏或内联函数封装
