Energy Indicator
==========================================

.. seealso::
  Init Function::

    from indicator.technology.energy import *
    import tushare as ts
    pro = ts.pro_api('59e1f90437c021fb31c99c20d08493070f17305afe606fdf0ef89f37')
    df = pro.daily(ts_code='000001.SZ', start_date='20180701', end_date='20190718')
    df['volume'] = df['vol']
    df.tail()

.. py:function:: BRAR(df, N=26)

  情绪指标

	#. BR>400，暗示行情过热，应反向卖出；BR<40 ，行情将起死回生，应买进
	#. AR>180，能量耗尽，应卖出；AR<40 ，能量已累积爆发力，应买进
	#. BR 由300 以上的高点下跌至50以下的水平,低于AR 时,为绝佳买点
	#. BR、AR、CR、VR 四者合为一组指标群，须综合搭配使用

	:param df: DataFrame
	:param N: 天数
	:return:
		:BR: 0和最高价-1日前的收盘价的较大值的N日累和/0和1日前的收盘价-最低价的较大值的N日累和*100
		:AR: 最高价-开盘价的N日累和/开盘价-最低价的N日累和*100

.. py:function:: CR(df, N=26, M1=10, M2=20, M3=40, M4=62)

	带状能量线

	#. CR>400时，其10日平均线向下滑落，视为卖出信号；CR<40买进
	#. CR 由高点下滑至其四条平均线下方时，股价容易形成短期底部
	#. CR 由下往上连续突破其四条平均线时，为强势买进点
	#. CR 除了预测价格的外，最大的作用在于预测时间
	#. BR、AR、CR、VR 四者合为一组指标群，须综合搭配使用

	:param df: DataFrame
	:param N: 带状能量线
	:param M1: 移动平均
	:param M2: 移动平均
	:param M3: 移动平均
	:param M4: 移动平均
	:return:
		:CR: 0和最高价-MID的较大值的N日累和/0和MID-最低价的较大值的N日累和*100
		:MA1: M1/2.5+1日前的CR的M1日简单移动平均
		:MA2: M1/2.5+1日前的CR的M2日简单移动平均
		:MA3: M1/2.5+1日前的CR的M3日简单移动平均
		:MA4: M1/2.5+1日前的CR的M4日简单移动平均

.. py:function:: MASS(df, N1=9, N2=25, M=6)

	梅斯线

	#. MASS>27 后，随后又跌破26.5，此时股价若呈上涨状态，则卖出；
	#. MASS<27 后，随后又跌破26.5，此时股价若呈下跌状态，则买进；
	#. MASS<20 的行情，不宜进行投资。

	:param df: DataFrame
	:param N1: 天数
	:param N2: 天数
	:param M: 移动平均
	:return:
		:MASS: 最高价-最低价的N1日简单移动平均/最高价-最低价的N1日简单移动平均的N1日简单移动平均的N2日累和
		:MAMASS: MASS的M日简单移动平均

.. py:function:: PSY(df, N=12, M=6)

	心理线

	#. PSY>75，形成Ｍ头时，股价容易遭遇压力
	#. PSY<25，形成Ｗ底时，股价容易获得支撑
	#. PSY 与VR 指标属一组指标群，须互相搭配使用

	:param df: DataFrame
	:param N: 心理线
	:param M: 移动平均
	:return:
		:PSY: 统计N日中满足收盘价>1日前的收盘价的天数/N*100
		:PSYMA: PSY的M日简单移动平均

.. py:function:: VR(df, N=26, M=6)

	成交量变异率

	#. VR>450，市场成交过热，应反向卖出
	#. VR<40 ，市场成交低迷，人心看淡的际，应反向买进
	#. VR 由低档直接上升至250，股价仍为遭受阻力，此为大行情的前兆
	#. VR 除了与PSY为同指标群外，尚须与BR、AR、CR同时搭配研判

	:param df: DataFrame
	:param N: 心理线
	:param M: 移动平均
	:return:
		:TH: 如果收盘价>1日前的收盘价,返回成交量(手),否则返回0的N日累和
		:TL: 如果收盘价<1日前的收盘价,返回成交量(手),否则返回0的N日累和
		:TQ: 如果收盘价=1日前的收盘价,返回成交量(手),否则返回0的N日累和
		:VR: 100*(TH*2+TQ)/(TL*2+TQ)
		:MAVR: VR的M日简单移动平均

.. py:function:: WAD(df, M=30)

	威廉多空力度线

	#. 股价一顶比一顶高，而WAD 一顶比一顶低，暗示头部即将形成
	#. 股价一底比一底低，而WAD 一底比一底高，暗示底部即将形成
	#. WAD 与OBV、ADVOL、ADL同属一组指标群，使用时应综合研判

	:param df: DataFrame
	:param M: 移动平均
	:return:
		:MIDA: 收盘价-1日前的收盘价和最低价的较小值
		:MIDB: 如果收盘价<1日前的收盘价,返回收盘价-1日前的收盘价和最高价的较大值,否则返回0
		:WAD: 如果收盘价>1日前的收盘价,返回MIDA,否则返回MIDB的历史累和
		:MAWAD: WAD的M日简单移动平均

.. py:function:: CYR(df, N=5, M=5)

	市场强弱

	#. CYR是成本均线派生出的指标,是13日成本均线的升降幅度
	#. 使用CYR可以对股票的强弱进行排序,找出其中的强势和弱势股票

	:param df: DataFrame
	:param M: 移动平均
	:return:
		:MIDA: 收盘价-1日前的收盘价和最低价的较小值
		:MIDB: 如果收盘价<1日前的收盘价,返回收盘价-1日前的收盘价和最高价的较大值,否则返回0
		:WAD: 如果收盘价>1日前的收盘价,返回MIDA,否则返回MIDB的历史累和
		:MAWAD: WAD的M日简单移动平均
