# VR Data Format
## Raw data format
 l:Transform matrix of left hand (16 floats) | r:Transform matrix of right hand (16 floats) |**hmd:Transform matrix of head (16 floats)**  & Left buttons, R buttons
 Left/Right buttons include Joystick(JS), Trigger(Trig), Gripper(Gripper), ...

## Format after processing by reader.py
```
({'hmd': array([[-9.99084e-01, -4.25241e-02,  4.82153e-03,  8.86887e-04],
       [ 1.23177e-02, -1.77830e-01,  9.83984e-01,  1.22044e+00],
       [-4.09856e-02,  9.83142e-01,  1.78191e-01,  1.91674e-03],
       [ 0.00000e+00,  0.00000e+00,  0.00000e+00,  1.00000e+00]]), 'l': array([[ 9.99997e-01, -8.11920e-04, -2.26379e-03,  9.40954e-04],
       [-8.03728e-04, -9.99993e-01,  3.61601e-03, -1.26086e-03],
       [-2.26671e-03, -3.61419e-03, -9.99991e-01,  1.99884e-01],
       [ 0.00000e+00,  0.00000e+00,  0.00000e+00,  1.00000e+00]]), 'r': array([[ 9.99997e-01,  8.11920e-04,  2.26379e-03,  9.40954e-04],
       [-8.03728e-04,  9.99993e-01, -3.61601e-03, -1.26086e-03],
       [-2.26671e-03,  3.61419e-03,  9.99991e-01,  1.99884e-01],
       [ 0.00000e+00,  0.00000e+00,  0.00000e+00,  1.00000e+00]])}, {'A': False, 'B': False, 'RThU': False, 'RJ': False, 'RG': False, 'RTr': False, 'X': False, 'Y': False, 'LThU': False, 'LJ': False, 'LG': False, 'LTr': False, 'leftJS': (0.0, 0.0), 'leftTrig': (0.0,), 'leftGrip': (0.0,), 'rightJS': (0.0, 0.0), 'rightTrig': (0.0,), 'rightGrip': (0.0,)})
```

# VR Data Format (original)

## Raw data format
 l:Transform matrix of left hand (16 floats) | r:Transform matrix of right hand (16 floats) & Left buttons, R buttons
 Left/Right buttons include Joystick(JS), Trigger(Trig), Gripper(Gripper), ...

## Format after processing by reader.py
```
({'l': array([[ 1.00000e+00, -1.28818e-05, -1.26675e-04, -1.06146e-04],
       [-1.28352e-05, -1.00000e+00,  3.62815e-04, -5.85318e-05],
       [-1.26690e-04, -3.62818e-04, -1.00000e+00,  2.00233e-01],
       [ 0.00000e+00,  0.00000e+00,  0.00000e+00,  1.00000e+00]]), 'r': array([[ 1.00000e+00,  1.28818e-05,  1.26690e-04, -1.06146e-04],
       [-1.28361e-05,  1.00000e+00, -3.62815e-04, -5.85318e-05],
       [-1.26675e-04,  3.62818e-04,  1.00000e+00,  2.00233e-01],
       [ 0.00000e+00,  0.00000e+00,  0.00000e+00,  1.00000e+00]])}, {'A': False, 'B': False, 'RThU': False, 'RJ': False, 'RG': False, 'RTr': False, 'X': False, 'Y': False, 'LThU': False, 'LJ': False, 'LG': False, 'LTr': False, 'leftJS': (0.0, 0.0), 'leftTrig': (0.0,), 'leftGrip': (0.0,), 'rightJS': (0.0, 0.0), 'rightTrig': (0.0,), 'rightGrip': (0.0,)})
```

`'l'`:左手的变换矩阵
`'r'`:右手的变换矩阵

剩余是按钮，含义如下表所示：

| 键              | 含义           |
| -------------- | ------------ |
| `A`, `B`       | 右手 AB 键      |
| `X`, `Y`       | 左手 XY 键      |
| `LJ`, `RJ`     | 摇杆按压         |
| `LThU`, `RThU` | 拇指触控         |
| `LG`, `RG`     | Grip 是否被按    |
| `LTr`, `RTr`   | Trigger 是否被按 |

## 转换成机械臂的action格式

`action[7] = [x, y, z, roll, pitch, yall, gripper]`

`gripper`是指夹爪的状态：
- `0.0`：松开
- `1.0`：关闭