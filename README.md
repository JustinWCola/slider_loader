# 载玻片装载器

## 执行机构部分

- 电机选型：N20电机带编码器
- 驱动芯片：TB6612
- 硬件连接：

| 单片机(IO) | 驱动    | 电机  |
|---------|-------|-----|
| CW(7)   | AIN1  |     |
| CCW(8)  | AIN2  |     |
| PWM(9)  | PWMA  |     |
| 5V      | STBY  | VCC |
| GND     | GND   | GND |
|         | AOUT1 | M1  |
|         | AOUT2 | M2  |
| EA(2)   |       | C1  |
| EB(3)   |       | C2  |

- 软件逻辑：
  - 硬件中断读取编码器值
  - 普通IO口控制电机方向
  - 输出PWM控制电机速度
  - 位置环PID控制，限位开关复位

## 传送机构部分

### NiMotion电机

- 通信协议测试中

| COB-ID                 | 0   | 1  | 2-3 | 4-7 |
|------------------------|-----|----|-----|-----|
| 发送 600+ID<br/>接收580+ID | 命令符 | 索引 | 子索引 | 数据  |

