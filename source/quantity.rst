Quantity and price Indicators
==========================================

.. seealso::
  Init Function::

    from indicator.technology.quantity import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    df['volume'] = df['vol']
    df.tail()
    dp = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    dp['volume'] = dp['vol']
    dp.tail()

.. py:function:: AMO(df, M1=5, M2=10)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :param M1: 移动平均
  :param M2: 移动平均
  :return:
    :AMOW: 成交额(元)/10000.0
    :AMO1: AMOW的M1日简单移动平均
    :AMO2: AMOW的M2日简单移动平均

  .. note:: 
    成交金额

    #. 成交金额大，代表交投热络，可界定为热门股
    #. 底部起涨点出现大成交金额，代表攻击量
    #. 头部地区出现大成交金额，代表出货量
    #. 观察成交金额的变化，比观察成交手数更具意义，因为成交手数并未反应股价的涨跌的后所应支出的实际金额

.. py:function:: OBV(df, M=30)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :param M: 移动平均
  :return:
    :OBV: 如果收盘价=1日前的收盘价,返回0,否则返回(如果收盘价>1日前的收盘价,返回成交量(手),否则返回-成交量(手))的历史累和
    :MAOBV: OBV的M日简单移动平均

  .. note::
    累积能量线

    #. 股价一顶比一顶高，而OBV 一顶比一顶低，暗示头部即将形成
    #. 股价一底比一底低，而OBV 一底比一底高，暗示底部即将形成
    #. OBV 突破其Ｎ字形波动的高点次数达5 次时，为短线卖点
    #. OBV 跌破其Ｎ字形波动的低点次数达5 次时，为短线买点
    #. OBV 与ADVOL、WAD、ADL同属一组指标群，使用时应综合研判

.. py:function:: VOL(df, M1=5, M2=10)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :return:
    :VOLUME: 成交量(手)
    :MA5: VOLUME的M1日简单移动平均
    :MA10: VOLUME的M1日简单移动平均

  .. note::
    成交量

.. py:function:: VRSI(df, N1=6, N2=12, N3=24)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :param N1: 相对强弱量
  :param N2: 相对强弱量
  :param N3: 相对强弱量
  :return:
    :RSI1: 成交量(手)-1日前的成交量和0的较大值的N1日[1日权重]移动平均/成交量(手)-1日前的成交量的绝对值的N1日[1日权重]移动平均*100
    :RSI2: 成交量(手)-1日前的成交量和0的较大值的N2日[1日权重]移动平均/成交量(手)-1日前的成交量的绝对值的N2日[1日权重]移动平均*100
    :RSI3: 成交量(手)-1日前的成交量和0的较大值的N3日[1日权重]移动平均/成交量(手)-1日前的成交量的绝对值的N3日[1日权重]移动平均*100

  .. note::
    相对强弱量

    #. VRSI>20 为超买；VRSI<20 为超卖
    #. VRSI 以50为中界线，大于50视为多头行情，小于50视为空头行情
    #. VRSI 在80以上形成Ｍ头或头肩顶形态时，视为向下反转信号
    #. VRSI 在20以下形成Ｗ底或头肩底形态时，视为向上反转信号
    #. VRSI 向上突破其高点连线时，买进；VRSI 向下跌破其低点连线时，卖出

.. py:function:: DBQRV(df, dp, N=5)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :param N: 对比强弱量
  :return:
    :ZS: (大盘的成交量-N日前的大盘的成交量)/N日前的大盘的成交量
    :GG: (成交量(手)-N日前的成交量(手))/N日前的成交量(手)

  .. note::
    对比强弱量

.. py:function:: DBLB(df, dp, N=5)
  :module: indicator.technology.quantity

  :param df: DataFrame
  :param N: 对比量比
  :param M: 移动平均
  :return:
    :DBLB: 输出对比量比
    :MADBLB: DBLB的M日简单移动平均

  .. note::
    对比量比

    * 对比量比指标用于用于测度成交量放大程度或萎缩程度的指标
    * 对比量比值越大，说明成交量较前期成交量放大程度越大，对比量比值越小，说明成交量较前期成交量萎缩程度越大

    一般认为:

    #. 对比量比大于20可以认为成交量极度放大；
    #. 对比量比大于3,可以认为成交量显著放大；
    #. 对比量比小于0.2,可以认为成交量极度萎缩；
    #. 对比量比小于0.4,可以认为成交量显著萎缩。
