## Pytest单元测试

pytest是一个帮助你写出更好程序的工具—非常方便的写小的测试集

1. 一个简单的例子

```
def inc(x):
    return x+1
def test_answer():
    assert inc(3) == 5
```

2. 安装

   ```
   pip install -U pytest
   ```

   检查是否安装成功

   ```
   pytest --version
   This is pytest version 3.x.y, imported from $PYTHON_PREFIX/lib/python3.5/site-packages/pytest.py
   ```

3. pytest将会在当前目录下运行所有的以`test__*.py`或者`*_test.py`

   * 可以将多个方法写在同一个class中

     ```
     class TestClass(object):
         def test_one(self):
             x = "this"
             assert 'h' in x

         def test_two(self):
             x = "hello"
             assert hasattr(x, 'check')
     ```

4. pytest中命令

   * 6种不同的返回码
     0. 所以的测试用例都成功通过
     1. 其中有一些测试未通过
     2. 测试被用户中断
     3. 测试被内部错误所中断
     4. pytest命令行用法错误
     5. 没有收集到任何一个测试

   `pytest —fixture` 显示所以可用的内置功能参数

   `pytest -h | —help` 在命令行中显示帮助菜单

5. `pytest -x` 在首次失败后终止运行

   `pytest —maxfail=2` 在两次失败后终止运行

6. `pytest test_mod.py` 以组件方式运行

   `pytest testing/` 运行目录

   `pytest -k "MyClass and not method"` 运行测试并且抛出关键字异常

7. `::` 运行测试中的节点

   `pytest test_mod.py::test_func`

   `pytest test_mod.py::TestClass::test_method`

   `pytest -m slow`相当于`@pytest.mark.slow`运行标记异常的错误

8. 修改python中追溯打印

   ```
   pytest --showlocals # show local variables in tracebacks
   pytest -l           # show local variables (shortcut)

   pytest --tb=auto    # (default) 'long' tracebacks for the first and last
                        # entry, but 'short' style for the other entries
   pytest --tb=long    # exhaustive, informative traceback formatting
   pytest --tb=short   # shorter traceback format
   pytest --tb=line    # only one line per failure
   pytest --tb=native  # Python standard library formatting
   pytest --tb=no      # no traceback at all
   ```

9. pytest也可以用`--pdb`去调试

   ```
   pytest -x --pdb   # drop to PDB on first failure, then end test session
   pytest --pdb --maxfail=3  # drop to PDB for first three failures

   设置断点
   import pdb
   pdb.set_tract()
   ```

   ​