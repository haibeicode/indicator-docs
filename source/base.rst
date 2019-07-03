Base Function
==========================================

.. seealso::
   Init Function::

		from indicator.base import *
		import pandas as pd
		a = [1, 2, 3, 4, 5, 6, 7]
		b = [2, 1, 6, 8, 4, 3, 9]
		df = pd.DataFrame({'a': a, 'b': b})
		df

.. py:function:: IF(logic, a, b)

	逻辑取值

	:param logic: logic
	:param a: DataFrame
	:param b: DataFrame
	:rtype: DataFrame

	example ::

		IF(df['a'] > df['b'], df['a'], df['b'])

.. py:function:: IFAND(logic1, logic2, a, b)

	逻辑和

	:param logic1: logic1
	:param logic2: logic2
	:param a: DataFrame
	:param b: DataFrame
	:rtype: DataFrame

	example ::

		IFAND(df['a'] > df['b'], df['a'] > 5, df['a'], df['b'])

.. py:function:: MAX(a, b)

	求最大值
	
	:param a: DataFrame
	:param b: DataFrame
	:rtype: DataFrame

	example ::

		MAX(df['a'], df['b']))

.. py:function:: MIN(a, b)

	求最小值

	:param a: DataFrame
	:param b: DataFrame
	:rtype: DataFrame

	example ::

		MIN(df['a'], df['b']))

.. py:function:: SUM(a, n=2)

	求总和

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		SUM(df['a'], 2)

.. py:function:: COUNT(logic, n=2)

	统计满足条件的周期数

	:param logic: logic
	:param n: Number
	:rtype: DataFrame

	example ::

		COUNT(df['a'] > 5, 2)

.. py:function:: STD(a, n=2)

	估算标准差

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		STD(df['a'], 2))

.. py:function:: ABS(a)

	求绝对值

	:param a: DataFrame
	:rtype: DataFrame

	example ::

		ABS(df['a'])

.. py:function:: AVEDEV(a, n=2)

	平均绝对偏差

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

      AVEDEV(df['a'], 2)

.. py:function:: CROSS(a, b)

	两条线交叉

	:param a: DataFrame
	:param b: DataFrame
	:rtype: DataFrame

	example ::

		CROSS(df['a'], df['b'])

.. py:function:: MA(a, n=2)

	简单移动平均

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		MA(df['a'], 2)

.. py:function:: SMA(a, n=2)

	移动平均

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		SMA(df['a'], 2)

.. py:function:: EMA(a, n=2)

	指数移动平均

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		EMA(df['a'], 2)

.. py:function:: HHV(a, n=2)

	求最高值

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		HHV(df['a'], 2)

.. py:function:: LLV(a, n=2)

	求最低值

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		LLV(df['a'], 2)

.. py:function:: REF(a, n=2)

	引用若干周期前的数据

	:param a: DataFrame
	:param n: Number
	:rtype: DataFrame

	example ::

		REF(df['a'], 2)
