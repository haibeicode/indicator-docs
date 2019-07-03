Overbought and Oversold
==========================================

.. seealso::
  Init Function::

    from indicator.technology.countertrend import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000837.SZ', start_date='20180701', end_date='20190718')
    df['volume'] = df['vol']
    df.tail()
    dp = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    dp.tail()

.. py:function:: CCI(df, N=14)

  商品路径指标

  #. CCI 为正值时，视为多头市场；为负值时，视为空头市场
  #. 常态行情时，CCI 波动于±100 的间；强势行情，CCI 会超出±100
  #. CCI>100 时，买进，直到CCI<100 时，卖出
  #. CCI<-100 时，放空，直到CCI>-100 时，回补

  :param df: DataFrame
  :param N: 天数
  :return:
		:TYP: (最高价+最低价+收盘价)/3
		:CCI: (TYP-TYP的N日简单移动平均)/(0.015*TYP的N日平均绝对偏差)

.. py:function:: KDJ(df, N=9, M1=3, M2=3)

  随机指标

  #. 指标>80 时，回档机率大；指标<20时，反弹机率大
  #. K在20左右向上交叉D时，视为买进信号
  #. K在80左右向下交叉D时，视为卖出信号
  #. J>100 时，股价易反转下跌；J<0 时，股价易反转上涨
  #. KDJ 波动于50左右的任何信号，其作用不大

  :param df: DataFrame
  :param N: 天数
  :param M1: 天数
  :param M2: 天数
  :return:
		:K: RSV的M1日[1日权重]移动平均
		:D: K的M2日[1日权重]移动平均
    :J: 3*K-2*D

.. py:function:: MFT(df, N=9)

  资金流量指标

  #. MFI>80 为超买，当其回头向下跌破80 时，为短线卖出时机
  #. MFI<20 为超卖，当其回头向上突破20 时，为短线买进时机
  #. MFI>80，而产生背离现象时，视为卖出信号
  #. MFI<20，而产生背离现象时，视为买进信号

  :param df: DataFrame
  :param N: 资金流量
  :return:
		:MFI: 如果TYP>1日前的TYP,返回TYP*成交量(手),否则返回0的N日累和/如果TYP<1日前的TYP,返回TYP*成交量(手),否则返回0的N日累和输出资金流量指标:100-(100/(1+V1))

.. py:function:: MTM(df, N=12, M=6)

  动量线

  #. MTM从下向上突破MTMMA，买入信号
  #. MTM从上向下跌破MTMMA，卖出信号
  #. 股价续创新高，而MTM未配合上升，意味上涨动力减弱
  #. 股价续创新低，而MTM未配合下降，意味下跌动力减弱
  #. 股价与MTM在低位同步上升，将有反弹行情；反之，从高位同步下降，将有回落走势

  :param df: DataFrame
  :param N: 资金流量
  :param M: 间隔天数，也是求移动平均的天数，一般取6
  :rtype: pandas DataFrame

.. py:function:: KD(df, N=9, M1=3, M2=3)

  随机指标

  :param df: DataFrame
  :param N: 天
  :param M1: 天
  :param M2: 天
  :param M: 资金流量
  :rtype: pandas DataFrame

.. py:function:: SKDJ(df, N=9, M=3)

  慢速随机指标

  #. 指标>80 时，回档机率大；指标<20 时，反弹机率大
  #. K在20左右向上交叉D时，视为买进信号
  #. K在80左右向下交叉D时，视为卖出信号
  #. SKDJ波动于50左右的任何讯号，其作用不大

  :param df: DataFrame
  :param N: 天
  :param M: 天
  :rtype: pandas DataFrame

.. py:function:: UDL(df, N1=3, N2=5, N3=10, N4=20, M=6)

  引力线

  #. 本指标的超买超卖界限值随个股不同而不同，使用者应自行调整
  #. 使用时，可列出一年以上走势图，观察其常态性分布范围，然后用参考线设定其超买超卖范围
  通常UDL 高于某个极限时，短期股价会下跌；UDL 低于某个极限时，短期股价会上涨
  #. 本指标可设参考线

  :param df: DataFrame
  :param N1: 天
  :param N2: 天
  :param N3: 天
  :param N4: 天
  :param M: 天移动平均
  :rtype: pandas DataFrame

.. py:function:: WR(df, N=10, N1=6)

  威廉指标

  #. WR波动于0 - 100，100置于顶部，0置于底部
  #. 本指标以50为中轴线，高于50视为股价转强；低于50视为股价转弱
  #. 本指标高于20后再度向下跌破20，卖出；低于80后再度向上突破80，买进
  #. WR连续触底3 - 4次，股价向下反转机率大；连续触顶3 - 4次，股价向上反转机率大

  :param df: DataFrame
  :param N: 威廉指标
  :param N1: 威廉指标
  :rtype: pandas DataFrame

.. py:function:: LWR(df, N=9, M1=3, M2=3)

  威廉指标

  :param df: DataFrame
  :param N: 指数移动平均
  :param M1: 指数移动平均
  :param M1: 指数移动平均
  :rtype: pandas DataFrame

.. py:function:: BIASQL(df, N=6, M=6)

  乖离率-传统版

  :param df: DataFrame
  :param N: 乖离率
  :param M: 平均乖离率
  :rtype: pandas DataFrame

.. py:function:: BIAS(df, N1=6, N2=12, N3=24)

  乖离率

  #. 本指标的乖离极限值随个股不同而不同，使用者可利用参考线设定，固定其乖离范围
  #. 当股价的正乖离扩大到一定极限时，股价会产生向下拉回的作用力
  #. 当股价的负乖离扩大到一定极限时，股价会产生向上拉升的作用力
  #. 本指标可设参考线

  :param df: DataFrame
  :param N1: 乖离率
  :param N2: 乖离率
  :param N3: 乖离率
  :rtype: pandas DataFrame

.. py:function:: BIAS36(df, M=6)

  三六乖离

  #. 本指标的乖离极限值随个股不同而不同，使用者可利用参考线设定，固定其乖离范围。※一般6-12BIAS信号的可靠度比3-6BIAS佳
  #. 当股价的正乖离扩大到一定极限时，股价会产生向下拉回的作用力
  #. 当股价的负乖离扩大到一定极限时，股价会产生向上拉升的作用力
  #. 本指标可设参考线

  :param df: DataFrame
  :param M: 移动平均
  :rtype: pandas DataFrame

.. py:function:: ADTM(df, N=23, M=8)

  动态买卖气指标

  #. 该指标在+1到-1之间波动
  #. 低于-0.5时为很好的买入点,高于+0.5时需注意风险

  :param df: DataFrame
  :param N: 天
  :param M: 移动平均
  :rtype: pandas DataFrame

.. py:function:: ATR(df, N=14)

  真实波幅

  * 算法：今日振幅、今日最高与昨收差价、今日最低与昨收差价中的最大值，为真实波幅，求真实波幅的N日移动平均
  * 参数：N　天数，一般取14

  :param df: DataFrame
  :param N: 移动平均
  :rtype: pandas DataFrame

.. py:function:: DKX(df, M=10)

  多空线

  #. 当多空线上穿其均线时为买入信号
  #. 当多空线下穿其均线时为卖出信号

  :param df: DataFrame
  :param M: 移动平均
  :rtype: pandas DataFrame

.. py:function:: TAPI(df, dp, M=6)

  多空线

  #. 先界定TAPI长期以来经常性的高低极限值，当TAPI触及顶端极限时，股价可能形成头部
  当TAPI触及底端极限时，股价可能形成底部
  #. 行情上涨，TAPI应伴随上涨；若不升反跌，则近期内将面临回档
  #. 先前大盘量缩下跌，当其回升时，TAPI值却持续下跌，可视为买入信号

  :param df: DataFrame
  :param df: DataFrame
  :param M: TAPI
  :rtype: pandas DataFrame