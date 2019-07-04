Moving Average Function
==========================================

.. seealso::
  Init Function::

    from indicator.technology.average import *
    import tushare as ts
    df = ts.get_hist_data('000001')
    df.tail()

.. py:function:: BBI(df, M1=3, M2=6, M3=12, M4=24)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 天数
  :param M2: 天数
  :param M3: 天数
  :param M4: 天数
  :return:
    :BBI: (收盘价的M1日简单移动平均+收盘价的M2日简单移动平均+收盘价的M3日简单移动平均+收盘价的M4日简单移动平均)/4

  .. note:: 
    多空均线

    #. 股价位于BBI 上方，视为多头市场
    #. 股价位于BBI 下方，视为空头市场

.. py:function:: EXPMA(df, P1=5, P2=10, P3=20, P4=60)
  :module: indicator.technology.average

  :param df: DataFrame
  :param P1: 指数平均线
  :param P2: 指数平均线
  :param P3: 指数平均线
  :param P4: 指数平均线
  :return:
    :EXP1: 收盘价的M1日指数移动平均
    :EXP2: 收盘价的M2日指数移动平均

  .. note:: 
    指数平均线

    #. EXPMA 一般以观察12日和50日二条均线为主
    #. 12日指数平均线向上交叉50日指数平均线时，买进
    #. 12日指数平均线向下交叉50日指数平均线时，卖出
    #. EXPMA 是多种平均线计算方法的一
    #. EXPMA 配合MTM 指标使用，效果更佳

.. py:function:: HMA(df, M1=6, M2=12, M3=30, M4=72, M5=144)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 高价平均线
  :param M2: 高价平均线
  :param M3: 高价平均线
  :param M4: 高价平均线
  :param M5: 高价平均线
  :return:
    :HMA1: 最高价的M1日简单移动平均
    :HMA2: 最高价的M2日指数移动平均
    :HMA3: 最高价的M3日指数移动平均
    :HMA4: 最高价的M4日指数移动平均
    :HMA5: 最高价的M5日指数移动平均

  .. note:: 
    高价平均线

    一般移动平均线以收盘价为计算基础，高价平均线是以每日最高价为计算基础，目前市场上许多投资人将其运用在空头市场，认为它的压力效应比传统平均线更具参考价值

.. py:function:: LMA(df, M1=6, M2=12, M3=30, M4=72, M5=144)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 低价平均线
  :param M2: 低价平均线
  :param M3: 低价平均线
  :param M4: 低价平均线
  :param M5: 低价平均线
  :return:
    :LMA1: 最低价的M1日简单移动平均
    :LMA2: 最低价的M2日指数移动平均
    :LMA3: 最低价的M3日指数移动平均
    :LMA4: 最低价的M4日指数移动平均
    :LMA5: 最低价的M5日指数移动平均

  .. note:: 
    低价平均线

    一般移动平均线以收盘价为计算基础，低价平均线是以每日最低价为计算基础目前市场上许多投资人将其运用在多头市场，认为它的支撑效应比传统平均线更具参考价值

.. py:function:: VMA(df, M1=6, M2=12, M3=30, M4=72, M5=144)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 变异平均线
  :param M2: 变异平均线
  :param M3: 变异平均线
  :param M4: 变异平均线
  :param M5: 变异平均线
  :return:
    :VMA1: (最高价+开盘价+最低价+收盘价)/4 的M1日简单移动平均
    :VMA2: (最高价+开盘价+最低价+收盘价)/4 的M2日指数移动平均
    :VMA3: (最高价+开盘价+最低价+收盘价)/4 的M3日指数移动平均
    :VMA4: (最高价+开盘价+最低价+收盘价)/4 的M4日指数移动平均
    :VMA5: (最高价+开盘价+最低价+收盘价)/4 的M5日指数移动平均

  .. note:: 
    变异平均线

    #. 股价高于平均线，视为强势；股价低于平均线，视为弱势
    #. 平均线向上涨升，具有助涨力道；平均线向下跌降，具有助跌力道
    #. 二条以上平均线向上交叉时，买进
    #. 二条以上平均线向下交叉时，卖出
    #. VMA 比一般平均线的敏感度更高，消除了部份平均线落后的缺陷

.. py:function:: AMV(df, M1=5, M2=13, M3=34, M4=60)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 成本价均线
  :param M2: 成本价均线
  :param M3: 成本价均线
  :param M4: 成本价均线
  :return:
    :AMV1: 成交量(手)*(开盘价+收盘价)/2 的M1日累和/成交量(手)的M1日累和
    :AMV2: 成交量(手)*(开盘价+收盘价)/2 的M2日累和/成交量(手)的M1日累和
    :AMV3: 成交量(手)*(开盘价+收盘价)/2 的M3日累和/成交量(手)的M1日累和
    :AMV4: 成交量(手)*(开盘价+收盘价)/2 的M4日累和/成交量(手)的M1日累和

  .. note:: 
    成本价均线

    * 成本价均线不同于一般移动平均线系统，成本价均线系统首次将成交量引入均线系统，充分提高均线系统的可靠性
    * 同样对于成本价均线可以使用月均线系统(5,10,20,250)和季均线系统(20,40,60,250),另外成本价均线还可以使用自身特有的均线系统(5,13,34,250),称为市场平均建仓成本均线，简称成本价均线
    * 在四个均线中参数为250的均线为年度均线,为行情支撑均线
    * 成本均线不容易造成虚假信号或骗线，比如某日股价无量暴涨，移动均线会大幅拉升，但成本均线却不会大幅上升，因为在无量的情况下市场持仓成本不会有太大的变化
    * 依据均线理论，当短期均线站在长期均线之上时叫多头排列，反之就叫空头排列
    * 短期均线上穿长期均线叫金叉，短期均线下穿长期均线叫死叉
    * 均线的多头排列是牛市的标志，空头排列是熊市的标志
    * 均线系统一直是市场广泛认可的简单而可靠的分析指标，其使用要点是尽量做多头排列的股票，回避空头排列的股票
    * 34日成本线是市场牛熊的重要的分水岭。一旦股价跌破34日成本线，则常常是最后的出逃机会

.. py:function:: BBIBOLL(df, N=11, M=6)
  :module: indicator.technology.average

  :param df: DataFrame
  :param N: 天数
  :param M: 天数
  :return:
    :BBIBOLL: (收盘价的3日简单移动平均+CV的6日简单移动平均+CV的12日简单移动平均+CV的24日简单移动平均)/4
    :UPR: BBIBOLL+M*BBIBOLL的N日估算标准差
    :DWN: BBIBOLL-M*BBIBOLL的N日估算标准差

  .. note:: 
    多空布林线

    BBI算法：3日平均价加6日平均价加12日平均价加24日平均价，其和除以四

    用法：

    #. 为BBI与BOLL的迭加
    #. 高价区收盘价跌破BBI线，卖出信号
    #. 低价区收盘价突破BBI线，买入信号
    #. BBI线向上，股价在BBI线之上，多头势强
    #. BBI线向下，股价在BBI线之下，空头势强

.. py:function:: ALLIGAT(df, M1=13, M2=8, M3=5)
  :module: indicator.technology.average

  :param df: DataFrame
  :param M1: 平滑移动均线
  :param M2: 平滑移动均线
  :param M3: 平滑移动均线
  :return:
    :BBIBOLL: 3日前的(最高价+最低价)/2的5日简单移动平均
    :UPR: 5日前的(最高价+最低价)/2的5日简单移动平均
    :DWN: 8日前的(最高价+最低价)/2的5日简单移动平均

  .. note:: 
    鳄鱼线

    * 鳄鱼线是运用分形几何学和非线性动力学的一组平均线（实际上就是一种比较特别的均线）,它分为蓝、红、绿三条
    * 蓝线被称为鳄鱼的颚部，红线被称为鳄鱼的牙齿，绿色被称为鳄鱼的唇吻

    它们的构造方法如下：

    * 颚部——13根价格线的平滑移动均线，并将数值向未来方向移动8根价格线
    * 牙齿——8根价格线的平滑移动平均线，并将数值向未来方向移动5根价格线
    * 唇吻——5根价格线的平滑移动均线，并将数值向未来方向移动3根价格线

    鳄鱼线的基本使用方法是：

    #. 当颚部、牙齿、唇吻纠缠在一起时，我们便进入了观望期（鳄鱼休息了）
    #. 当唇吻(绿）在牙齿（红）以上，牙齿在颚部（蓝）以上时，我们便进入了多头市场（颚鱼要开始吃牛肉了）
    #. 当唇吻在牙齿以下，牙齿在颚部以下时，我便进入了空头市场（鳄鱼要开始吃熊肉了）
