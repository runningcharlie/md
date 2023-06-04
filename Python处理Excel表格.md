Pandas

    什么是Pandas

        Pandas：Python的一个第三方库，是一个数据分析库。
        Pandas提供了数据清洗、数据准备和数据分析功能
        Dataframe：在python代码中创建和管理的数据表
        Series：数据表中的每一列
        pandas可以将数据从excel工作簿加载到Dataframe
        加载数据 - 查看数据 - 处理数据（检查数据、数据排序、数据筛选、清理数据）- 导出到excel

    安装pandas

        pip install pandas
        pip install openpyxl

    加载并保存数据

        读取文件

            import pandas as pd
            df_csv = pd.read_csv("数据集.csv")  读取csv文件
            df_xlsx = pd.read_excel("人力资源数据.xlsx", sheet_name="新入职员工", header=None)

            注释:
            读取Excel文件；只有一个参数默认读取第一个工作表。
            如需读取指定工作表，则添加第二个参数sheet_name；
            panda会默认把第一行数据当作标题行来处理。
            传入第三个参数header去掉默认行为

            print(df_xlsx)
            df_xlsx.columns = ["员工编号","员工姓名","办公楼","电话","部门","状态","入职日期","在职年数","福利代码","年薪",]  添加Dataframe列名（excel表头）

        导出文件

            df_xlsx.to_excel("导出\新员工.xlsx", index=None)  保存数据到Excel文件
                参数格式：导出目录\文件名（注意是反斜杠）
                默认导出工作表的每行数据会自带索引，如需去掉，则传入第二个参数index=None

    查看数据

        查看dataframe中的所有数据

            import pandas as pd
            pd.set_option("display.max_rows", None)

        对齐表格

            tabulate库：对齐终端窗格中的数据
            wcwidth库：确保中文内容能正常对齐

            import pandas as pd
            from tabulate import tabulate  从tabulate模块引入tabulate函数

            df = pd.read_excel("人力资源数据.xlsx", sheet_name="人力资源")
            print(tabulate(df, headers='keys'))   设置表头参数：headers='keys' -> 使用Dataframe列名作为表头

        快速查看数据

            print(df.columns)   查看所有列名
            print(df.shape)   获取dataframe的大小（数据表有几行几列）
            print(df.head())   快速查看dataframe前几行数据(返回前5行数据)
            print(df[0:5])   通过索引返回指定行数的数据，效果和head方法相同

        访问指定位置数据

            使用 pandas 索引器 iloc 访问指定位置的数据

                import pandas as pd
                from tabulate import tabulate


                df = pd.read_excel('人力资源数据.xlsx', sheet_name='人力资源')
                print(tabulate(df, headers='keys'))
                print(df.shape)

                返回单元格 -> 第741行，第10列
                object_name.iloc[[行索引,行索引,...], [列索引,列索引,...]]
                第 741 行的索引值是740, 第10列的索引值是9
                print(df.iloc[740, 9])

                返回区域 -> 倒数第4行到倒数第2行, 第2列到第4列的数据
                print(df.iloc[737:740, 1:4])

                返回行或列
                print(df.iloc[739, :])  # 返回整列
                print(df.iloc[:, 1])  # 返回整行

#### 筛选和排序

**筛选**

```python
import pandas as pd
from tabulate import tabulate

df = pd.read_excel("人力资源数据.xlsx", sheet_name="人力资源")

# 查看dataframe每列的数据类型
print(df.dtypes)

# 筛选 - 单个条件
print(df["员工编号"] > 1700)  # 返回包含布尔值的series对象
print(df[df["员工编号"] > 1700])  # 将筛选条件作为参数传入dataframe -> 返回结果
print(tabulate(df[df["员工编号"] > 1700], headers="keys")) # 格式化输出结果

# 筛选 - 多个条件
# 注意每个条件都要用小括号包裹
print(tabulate(df[(df["员工编号"] > 1700) & (df["入职日期"] > '2021-7-1')], headers="keys")) # 且 需要同时满足两个条件
print(tabulate(df[(df["员工编号"] > 1700) | (df["入职日期"] > '2021-7-1')], headers="keys")) # 或 只需满足一个条件
```

**排序**

使用 sort_values 方法对 dataframe 进行排序

```py
import pandas as pd
from tabulate import tabulate

df = pd.read_excel('人力资源数据.xlsx', sheet_name='人力资源')
# print(tabulate(df, headers='keys'))

# object_name.sort_values(by=[index value], ascending=[False])
# 从DataFrame对象调用.sort_values()方法，通过by参数指定进行排序的列, 通过ascending参数控制进行升序或降序排序
print(tabulate(df.sort_values(by="办公楼"), headers="keys"))

# 根据多个条件排序 -> 将多个列名以列表的形式传入by参数
print(tabulate(df.sort_values(by=["办公楼", "在职年数"]), headers="keys"))

# 降序排序 -> ascending设置为False
print(tabulate(df.sort_values(by=["办公楼", "在职年数"], ascending=False), headers="keys"))

# 每列按照不同的升降序排序 -> 将多个布尔值以列表的形式传入ascending参数
print(tabulate(df.sort_values(by=["办公楼", "在职年数"], ascending=[True, False]), headers="keys"))
```

#### 清理数据

#### 数据汇总

### openpyxl

### Pandas 和 openpyxl
