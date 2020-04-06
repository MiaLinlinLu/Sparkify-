# Sparkify 流失用户预测

## 数据集介绍

* 该数据集（128MB）是Sparikify在2018年10月1日-12月3日的用户日志，其中记录内容包括：artist, auth, firstName, gender, itemInSession, lastName, length, level, location, method, page, registration, sessionId, song, status, ts, userAgent, userId

## 项目目的
* 根据用户数据集预测流失用户

## 项目分析步骤
### 探索数据
* 定义`page`值为'Cancellation Confirmation'的客户为流失客户。
* 清除`userId`值为空字符串的数据
* 找到流失客户的userId
* 计算客户流失率：流失客户数量/总客户数量
* 用户活跃时间可视化

### 特征工程- 共选择了20个features
* 用户的活跃程度（每个用户在用户日志中出现条目的个数）
* 用户的活跃时间跨度 （日志中，每个用户最晚记录和最早记录的时间差）
* `page`中各个状态的出现频率。这些状态包括：'About', 'Add Friend', 'Add to Playlist', 'Downgrade', 'Error', 'Help', 'Home', 'Logout', 'NextSong', 'Roll Advert', 'Save Settings', 'Settings', 'Submit Downgrade', 'Submit Upgrade', 'Thumbs Down', 'Thumbs Up', 'Upgrade'
* 用户的活跃频率（活跃程度/活跃时间跨度）

### 建模
* 分别采用了逻辑回归和决策树两种机器学习方法进行建模。
* 并对结果进行了评估，评估参数为：accuracy, precision, recall, F1score.
* 结果：在最后选用的决策树方法中，在验证集上的accuracy,precision,recall和F1score均为1

### 测试
* 利用上一步得到的决策树模型对测试集进行了预测，结果accuracy, precision, recall, F1score均为1。

### 总结
选用特征工程中所写参数，构造的决策树模型可以非常好地预测流失用户。
