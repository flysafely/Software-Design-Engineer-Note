### 基本概念
  + 概念数据模型
    > 也称信息模型：E-R模型（实体-联系模型）<br>
      用于第一层抽象现实-信息世界，用于数据库设计
  + 基本数据模型
### 数据模型的三要素
  + 数据结构
  + 数据操作
  + 数据约束条件
---
### E-R模型
  + **实体**<br>
    ![9-2](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-2.jpg)
    > 用矩形表示<br>
      矩形内写实体名<br>
      区别于其他对象的事件或物体<br>
    + 弱实体<br>
      ![9-3](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-3.jpg)
      > 这类实体的存在必须以另外一个实体为前提
      + 图示<br>
      ![9-1](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-1.jpg)
  + **联系**<br>
    ![9-6](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-6.jpg)
    > 用菱形表示<br>
      菱形框中写联系名<br>
      用无向边分别连接有关实体<br>
      用(1:1,1:n,m:n)在无向边上标注联系的类型<br>
    + **联系不是关系、关系模式**
      + **联系**:`实体内部的联系反映数据在同一记录内部各字段间的联系`
      + **关系模式**:`静态的描述该模式下的所有关系，例如数据表中的字段表头`
      + **关系模型**:`若干关系模式组成的集合`
      + **关系**:`动态的反映一个时刻、状态的信息，例如数据表中的某条数据
                  在关系模型中实体与实体间的联系是用关系来描述的`
      + **关系数据库**:`是按照关系模型建立的数据库`
      ---
      + **实例、联系转关系模式**★★★
        + **E-R图联系中的1:1**<br>
          > 可以将联系关系模式合并到任意一个实体关系模式中
        ![9-15](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-15.png)
        + **E-R图联系中的1:n**<br>
          > 可以将联系关系模式合并到多端的实体关系模式中
        ![9-16](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-16.jpg)
        + **E-R图联系中的m:n**<br>
          > 只能将多对多中的联系单独成一个关系模式
        ![9-17](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-17.jpg)
    + 两个实体间的联系
      + 一对一：（1:1）<br>
      + 一对多：（1:n）<br>
      + 多对多：（m:n）<br>
    + 两个以上实体间的联系
      + 两两间的联系
        + 1：1：1<br>
        + 1：m：n<br>
        + r：m：n<br>
    + 同一实体间的二元联系<br>
      ![9-14](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-14.jpg)
    + 弱实体间的联系<br>
      ![9-7](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-7.jpg)
    + 联系集和实体连接<br>
    ![9-10](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-9.jpg)
    + 实体全部参与到联系中<br>
    ![9-10](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-10.jpg)
    + 
  + **属性**<br>
    ![9-4](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-4.jpg)
    > 用椭圆表示<br>
      实体某方面的特性<br>
    + 和实体连接<br>
    ![9-9](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-9.jpg)
    + 属性的分类
      + 简单属性
        > 原子、不可再分<br>
          不特别说明的话，默认为简单属性
      + 复合属性
        > 可以再划分为别的属性
      + 单值属性
        > 对于特定实体的某个属性只有一个单独的值，例如：<br>
          一个人只能有一个身份证号
      + 多值属性<br>
        ![9-5](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-5.jpg)
        > 对于特定的实体的某个属性可以有多个值，例如：<br>
          一个人可以有多个子女
      + NULL属性
        > 表示属性值未知，或无意义
      + 派生属性<br>
        ![9-8](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-8.jpg)
        > 派生属性可以从其他的属性得来，例如：<br>
          员工实体中有“参加工作时间”属性，要取得“工作年限”这个属性值，可以通过当前时间和“参加工作时间”属性值计算获得
  ---
### E-R模型扩充★★★
  + **特殊化**
    + 全部特殊化
      > 双实线连接圆圈
    + 部分特殊化
      > 单实线连接圆圈
    + 不相交特殊化
      > 圆圈中为d
    + 重叠特殊化
      > 圆圈中为o
    > 表示方式如下图<br>
  ![9-11](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-12.png)
  + 书中472页的图9-11应改为<br>
  ![9-13](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E4%B9%9D%E7%AB%A0-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%8A%80%E6%9C%AF%E5%9F%BA%E7%A1%80/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/9-13.jpg)

