Chart type 
==========================================

.. seealso::
  Init Function::

    from indicator.technology.chat import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20180718')
    df['volume'] = df['vol']
    df.tail()

.. py:function:: ZX(df)
  :module: indicator.technology.chat

  :param df: DataFrame
  :return:
    :AV: 0.01*成交额(元)/成交量(手)

  .. note:: 
    重心线

    * 重心线指标，重心线是由重心价连接而成的曲线，反映历史平均价位
    * 对于指数计算公式为: ZX = 成交金额/成交量
    * 对个股而言: ZX ＝ (最高指数＋最低指数＋收盘指数)/3
    * 类似于不加权平均指数


.. py:function:: PUCU(df, N=2)
  :module: indicator.technology.chat

  :param df: DataFrame
  :param N: 天数
  :return:
    :PU: 收盘价的N日简单移动平均
    :CU: 成交量(手)的N日简单移动平均

  .. note::     
    逆时钟曲线

    #. 图表的曲线上有一个箭头，该处代表目前价量的位置；
    #. 曲线由绿变成红色时，视为买进信号；
    #. 曲线由红变成绿色时，视为卖出信号。

