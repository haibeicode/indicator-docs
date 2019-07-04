God type
==========================================

.. seealso::
  Init Function::

    from indicator.technology.god import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    df['volume'] = df['vol']
    df.tail()
    dp = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    dp['volume'] = dp['vol']
    dp.tail()

.. py:function:: SGXDT(df, dp, P1=5, P2=10)
  :module: indicator.technology.god

  :param df: DataFrame
  :return:
    :QR: 收盘价/大盘的收盘价*1000
    :MQR1: QR的5日简单移动平均
    :MQR2: QR的10日简单移动平均

  .. note::
    心电图

.. py:function:: SGSMX(df, dp, N=50)
  :module: indicator.technology.god

  :param df: DataFrame
  :return:
    :ZY1: 收盘价/大盘的收盘价*2000 的3日指数移动平均
    :ZY2: 收盘价/大盘的收盘价*2000 的1日指数移动平均
    :ZY3: 收盘价/大盘的收盘价*2000 的34日指数移动平均
      
  .. note::
    生命线

.. py:function:: SGLB(df, dp)
  :module: indicator.technology.god

  :param df: DataFrame
  :return:
    :LB: 成交量(手)/大盘的成交量*1000
    :MA5: ZY2的5日简单移动平均
    :MA10: ZY2的10日简单移动平均

  .. note::
    量比

.. py:function:: SGPF(df, dp)
  :module: indicator.technology.god

  :param df: DataFrame
  :return:
    :PF: 输出强势股评分

  .. note::
    强势股评分
