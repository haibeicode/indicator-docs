Base Function
==========================================

.. seealso::
  Init Function::

    from indicator.base import *
    import pandas as pd
    a = [1, 2, 3, 4, 5, 6, 7]
    b = [2, 1, 6, 8, 4, 3, 9]
    df = pd.DataFrame({'a': a, 'b': b})

.. py:function:: IF(logic, a, b)
  :module: indicator.technology.base

  :param logic: logic
  :param a: DataFrame
  :param b: DataFrame
  :rtype: DataFrame

  .. note::
    逻辑取值

    example ::

      IF(df['a'] > df['b'], df['a'], df['b'])

.. py:function:: IFAND(logic1, logic2, a, b)
  :module: indicator.technology.base

  :param logic1: logic1
  :param logic2: logic2
  :param a: DataFrame
  :param b: DataFrame
  :rtype: DataFrame

  .. note::
    逻辑和

    example ::

      IFAND(df['a'] > df['b'], df['a'] > 5, df['a'], df['b'])

.. py:function:: MAX(a, b)
  :module: indicator.technology.base

  :param a: DataFrame
  :param b: DataFrame
  :rtype: DataFrame

  .. note::
    求最大值

    example ::

      MAX(df['a'], df['b']))

.. py:function:: MIN(a, b)
  :module: indicator.technology.base

  :param a: DataFrame
  :param b: DataFrame
  :rtype: DataFrame

  .. note::
    求最小值

    example ::

      MIN(df['a'], df['b']))

.. py:function:: SUM(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    求总和

    example ::

      SUM(df['a'], 2)

.. py:function:: COUNT(logic, n=2)
  :module: indicator.technology.base

  :param logic: logic
  :param n: Number
  :rtype: DataFrame

  .. note::
    统计满足条件的周期数

    example ::

      COUNT(df['a'] > 5, 2)

.. py:function:: STD(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    估算标准差

    example ::

      STD(df['a'], 2))

.. py:function:: ABS(a)
  :module: indicator.technology.base

  :param a: DataFrame
  :rtype: DataFrame

  .. note::
    求绝对值

    example ::

      ABS(df['a'])

.. py:function:: AVEDEV(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    平均绝对偏差

    example ::

        AVEDEV(df['a'], 2)

.. py:function:: CROSS(a, b)
  :module: indicator.technology.base

  :param a: DataFrame
  :param b: DataFrame
  :rtype: DataFrame

  .. note::
    两条线交叉

    example ::

      CROSS(df['a'], df['b'])

.. py:function:: MA(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    简单移动平均

    example ::

      MA(df['a'], 2)

.. py:function:: SMA(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    移动平均

    example ::

      SMA(df['a'], 2)

.. py:function:: EMA(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    指数移动平均

    example ::

      EMA(df['a'], 2)

.. py:function:: HHV(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    求最高值

    example ::

      HHV(df['a'], 2)

.. py:function:: LLV(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    求最低值

    example ::

      LLV(df['a'], 2)

.. py:function:: REF(a, n=2)
  :module: indicator.technology.base

  :param a: DataFrame
  :param n: Number
  :rtype: DataFrame

  .. note::
    引用若干周期前的数据

    example ::

      REF(df['a'], 2)
