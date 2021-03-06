# lec 3
## Python初步教程回顾
1. 四个空格锁紧
2. 基本内建类型
3. 基本数据结构
4. 条件语句
5. 循环
6. pip、模块、包
7. 主函数定义（相当于C中的main函数）
	* if __name__ == '__main__':
8. 类

## Python库
### numpy
### matplotlib
	1. 散点图
	2. 线图
	3. 虚线dash与图标legend
	4. subplot子图
### pandas
	1. 一维数据Series
	2. 二维数据DataFrame
### seaborn
	* seaborn更简洁，matplotlib更灵活
	1. 基于关系
	2. 基于分布
	3. 基于类别

## 多因子模型
1. 因子的来历 — 用于解释收益，“以少为美”
2. 因子投资的发展
	1. 单因子; CAPM, ect
	2. 多因子; Fama & French 3 factors, 5 factors, ect
	3. 市场异常回报; value, momentum, size, ect
	4. 因子投资; 以因子构建投资组合，提供因子回报
3. 美股因子的定义
	1. 历史上价值因子回报率最高（回撤幅度也最大）
	2. 所有因子检验中EW（等权）都高于VW（根据市值加权）
		* 说明小市值的回报高
4. 因子的特点：具有周期性
5. A股市场因子
	1. 定义的因子中不带负号的因子按从大到小排，带负号的按从小到大排
	2. 历史回测方法：做多前10%，做空后10%的投资组合
		* 对冲掉市场本身的波动，更能体现因子本身的作用
	3. 规模因子、反转因子表现好，价值因子表现差
6. 中美因子表现差异大
	1. 政策原因
	2. 投资者构成：美股机构为主，A股散户为主
7. 因子检验的一般方法：一维零投资组合检验
	1. 一维：单因子
	2. 零投资：做多做空结合
8. 多因子投资策略
9. 尝试用行为金融学理解因子回报
	1. 小市值——前景理论
	2. 高价值——过激反应 & 风险厌恶
	3. 高动量——反映不足 & 注意力偏差

## 创建自己的交易策略（海龟交易法）
### 趋势跟随
1. 趋势即动量因子
2. 何为趋势跟随
	1. 发现趋势“苗头”
	2. 顺着趋势方向下注
	3. 截断亏损，让利润奔跑
3. 系统性地开发一个完整的趋势策略
	1. 市场：买卖什么
	2. 头寸规模：买卖多少
		* 定义波动性 $N = (19*PDN + TR) / 20$
		  * PDN = 前一日的N值
		  * TR = 当日的真实波动幅度
		    * $TR = Max(H-L, H-PDC, PDC-L)$
		      * H = 当日最高价
		      * L = 当日最低价
		      * PDC = 前一日收盘价
		* 头寸规模 = 账户的1% / （N*每一点数所代表的美元）
		  * 每一点数所代表的美元>>>每一最小交易单位的资金（1手）
		* 风险与头寸单位
	3. 入市：什么时候买卖
		1. 以20日突破为基础的短期系统
		2. 以55日突破为基础的长期系统
		3. 逐步建仓
			1. 在突破点建立1个单位的头寸
			2. 按N/2的价格间隔逐步扩大头寸（以上一份订单的实际成交价为基准）
			3. 直到头寸达到规模上限
	4. 止损：什么时候放弃一个亏损头寸
		1. 任何一笔交易的风险程度不超过账户的2%
		2. 价格变动的上限就是2N，对于加仓情况，止损点上浮
	5. 退出：什么时候推出一个盈利头寸
		1. 10日反向突破推出
		2. 20日反向突破退出
	6. 战术：怎么买卖

评估策略看哪些指标
1. 最重要的两个指标
	1. 夏普比例
	2. 最大回撤 （时间、幅度）
2. 还有哪些值得关注
	1. 交易次数
	2. 信息率
	3. 年化收益
	4. 日均仓位
	5. …………