Ghost type
==========================================

.. seealso::
  Init Function::

    from indicator.technology.ghost import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    df['volume'] = df['vol']
    df.tail()

.. py:function:: CYS(df)
  :module: indicator.technology.ghost

  :param df: DataFrame
  :return:
    :CYC13: 0.01*成交额(元)的13日指数移动平均/成交量(手)的13日指数移动平均
    :CYS: (收盘价-CYC13)/CYC13*100

  .. note::
    成本均线

.. py:function:: CYW(df)
  :module: indicator.technology.ghost

  :param df: DataFrame
  :return:
    :CYW: 如果最高价>最低价,返回(收盘价-最低价/最高价-最低价+收盘价-最高价/最高价-最低价)*成交量(手),否则返回0的10日累和/10000

  .. note::
    成本均线
