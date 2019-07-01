Dragon type
==========================================

.. seealso::
  Init Function::

    from indicator.technology.chat import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20180718')
    df['volume'] = df['vol']
    df.tail()

.. py:function:: RAD(df, dp, D=3, S=30, M=30)

  威力雷达

  #. RAD 曲线往上跷升越陡者，代表该股为强势股。
  #. RAD 指标选择强势股的效果相当良好，请多多利用。

  :param df: DataFrame
  :param dp: DataFrame
  :param D: 天数
  :param S: 天数
  :param M: 天数
  :rtype: pandas DataFrame

.. py:function:: LON(df, N=10)

  逆时钟曲线

  #. 图表的曲线上有一个箭头，该处代表目前价量的位置；
  #. 曲线由绿变成红色时，视为买进信号；
  #. 曲线由红变成绿色时，视为卖出信号。

  :param df: DataFrame
  :param N: 天数
  :rtype: pandas DataFrame

.. py:function:: SHT(df, N=5)

  龙系短线

  #. 当指标曲线向上交叉其平均线时，视为短线买进信号。
  #. 当指标曲线向下交叉其平均线时，视为短线卖出信号。
  #. 本指标可搭配KDJ、DMA指标使用。

  :param df: DataFrame
  :param N: 天数
  :rtype: pandas DataFrame

.. py:function:: ZLJC(df)

  主力进出

  白线为短期主力运作轨迹，黄线为中期主力运作轨迹，紫线为长期主力运作轨迹。
  #. 主力进出指标的白线向上突破黄线、紫线且三线向上发散，表示主力有效控盘，可逢底介入，持股待涨。
  #. 主力进出指标的白线上涨过快远离黄、紫线，出现较大乖离，表示短线获利筹码较多，宜注意控制风险，可适当卖出。
  #. 当白线回落至黄、紫线处受支撑时，而黄紫线发散向上，表示上升趋势未改，前期股价回落仅是途中的回调，可适量跟进。
  #. 主力进出三线“死亡交叉”，盘口呈空头排列，投资者宜尽快出局。
  #. 主力进出三线相近并平行向下时，表明主力尚未进场或正在出货，此时不宜介入。
  #. 主力进出是一种趋势指标，但趋势改变信号有时会出现滞后现象，此时就要用主力买卖指标加以配合使用。

  :param df: DataFrame
  :rtype: pandas DataFrame

.. py:function:: ZLMM(df)

  主力买卖

  白线为短期趋势线，黄线为中期趋势线，紫线为长期趋势线。
  #. 主力买卖与主力进出配合使用时准确率极高。 
  #. 当底部构成发出信号，且主力进出线向上时判断买点，准确率极高。 
  #. 当短线上穿中线及长线时，形成最佳短线买点交叉形态（如底部构成已发出信号或主力进出线也向上且短线乖离率不大时）。
  #. 当短线、中线均上穿长线，形成中线最佳买点形态（如底部构成已发出信号或主力进出线也向上且三线均向上时）。 
  #. 当短线下穿中线，且短线与长线正乖离率太大时，形成短线最佳卖点交叉形态。 
  #. 当短线、中线下穿长线，且是主力进出已走平或下降时，形成中线最佳卖点交叉形态。
  #. 在上升途中，短、中线回落受长线支撑再度上行之时，为较佳的买入时机。
  #. 指标在0以上表明个股处于强势，指标跌穿0线表明该股步入弱势。

  :param df: DataFrame
  :rtype: pandas DataFrame

.. py:function:: ADVOL(df)

  龙系离散量

  :param df: DataFrame
  :rtype: pandas DataFrame