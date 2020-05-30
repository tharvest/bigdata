##### ARIMA 
**A**uto**R**egressive **I**ntegrated **M**oving **A**verage Model
自回归移动平均模型
ARIMA(p,d,q) 查分自回归移动平均模型：
    - AR自回归，p自回归项
    - MA移动平均，q移动平均项数
    - d为时间序列成为平稳是所做的差分次数
  
  ##### 基本思想

  将预测对象随时间推移而形成的数据序列视为一个随机序列，用一定的数据学模型来近似描述这个序列。这个模型一旦被识别后就可以从时间序列的过去只及现在值来预测未来值。现代统计方法、计量经济模型在某种程度上已经能够帮助企业对未来进行预测。

  ##### ARIMA模型预测的基本步骤
  