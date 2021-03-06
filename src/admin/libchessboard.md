# libchessboard

`libchessboard`是用c++写的chessboard模块. `src/libchessboard.so`是为x64 Linux编译的动态链接库(考虑到天梯赛很可能是在Linux上运行的).

据现有性能测试结果, 在随机数种子为114514时可以使比赛时间缩短1/3至1/2. 由于是熬夜写出来的, 性能测试非常水.

用法:
    其实现了原`constants.py`中`Chessboard`类的所有接口, 当做一个命名为`libchessboard.py`的python模块导入即可

依赖:
    libboost, libfmt

```python
    from libchessboard import Chessboard
    chessboard = Chessboard(list(some_random_sequence))
    # blablabla
```

| item  | use python chessboard | use libchessboard | speed up ratio |
| :---: | :-------------------: | :---------------: | :------------: |
| real  |        19.952s        |      8.589s       |     2.323      |
| user  |        18.101s        |      7.194s       |                |
|  sys  |        3.644s         |      2.851s       |                |

此外, 用pybind11重构的[yachessboard](https://github.com/HamiltonHuaji/yachessboard)(Yet Another Chessboard)可能更易于编译.

经测试发现, python 3.8(已知只对于ubuntu)以下的版本, 不能正确处理`__repr__`等魔术方法的导出, 所以需要3.8或以上版本, 或者用python再进行一些修补.
