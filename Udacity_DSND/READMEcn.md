# 项目构成

本项目需要你完成三个部分。

### 1.ETL 管道

在 Python 脚本 `process_data.py` 中，编写一个数据清洗管道，实现：

- 加载 `messages` 和 `categories` 数据集
- 将两个数据集进行合并 (merge)
- 清洗数据
- 将其存储到 SQLite 数据库中

### 2.机器学习管道

在 Python 脚本 `train_classifier.py` 中编写机器学习管道，实现：

- 从 SQLite 数据库中加载数据
- 将数据集分成训练和测试集
- 搭建文本处理和机器学习管道
- 使用 GridSearchCV 对模型进行训练和微调
- 输出测试集的结果
- 将最终的模型输出为 pickle 文件

### 3.Flask 网络应用程序

我们为你提供了 Flask 网络应用程序的大部分代码，你可以根据你学的 Flask 、HTML、CSS 和 JavaScript 知识自由地添加新特征。在本部分，你需要：

- 按需要修改数据库和模型的文件路径
- 使用 Poltly 向网络应用程序中添加数据可视化我们提供了一份示例代码给你。

### Github 与代码质量

你的项目还会根据下述标准评分：

- Git 和 Github 的使用
- 丰富的文档
- 代码干净且模块化

下面是每个部分的一些细节和提示，帮你快速上手。



# 数据管道：Jupyter Notebooks

我们在项目工作空间中提供了 Jupyter notebooks，里面有要求，会指导你如何上手两个数据管道。Jupyter notebook 不是提交时必须的，但是强烈建议在开始写 Python 脚本前完成它们。

### 项目工作环境 - ETL

数据管道的第一部分是提取、转换和加载流程。在这部分，你会读取数据集 ，清洗数据然后将它存储到 SQLite 数据库中。我们希望你用 pandas 实现数据清洗。为了将数据加载到 SQLite 数据库中，你可以使用 pandas 数据框的 `.to_sql()` 方法，该方法可以配合 SQLAlchemy 引擎使用。

你可以自由地进行数据探索性分析，找到如何清洗数据集的方法。尽管你不需要在项目提交中包括数据探索性分析内容，你需要将你的清洗代码包括在最后的 ETL 脚本 `process_data.py` 中。

### 项目工作空间 - 机器学习管道

对于机器学习的部分，你要将数据集分成训练集和测试集两部分。然后，你要使用 NLTK 和 scikit-learn 的 pipeline 与GridSearchCV 方法搭建一个机器学习管道，最后输出一个模型，该模型使用 `message` 列从36 个类别中进行多分类输出。最后，你要将你的模型导出为一个 pickle 文件。完成了该 notebook 之后，你需要将最终的机器学习代码包含到 `train_classifier.py` 中。



# 数据管道：Python 脚本

完成了 notebook 中的 ETL 和机器学习管道后，你需要将你的工作转移到 Python 脚本 `process_data.py` 和 `train_classifier.py` 中。如果以后有人要用更新过的或者全新的消息数据集，他们应该能够通过运行你的代码轻松地创建一个新模型。这些 Python 脚本应该能够接收额外的数据和模型的文件路径参数并正常运行。

#### 示例：

```txt
python process_data.py disaster_messages.csv disaster_categories.csv DisasterResponse.db

python train_classifier.py ../data/DisasterResponse.db classifier.pkl
```

课程主页里的资源 (Resources) 部分提供了这些脚本的模板以及 **项目工作环境 IDE**。模板中给出了处理这些命令行参数的代码。



# Flask App

最后一步，你要用 Flask 网络应用程序展示你的结果。我们为你提供了工作环境，其中包含了一些原始文件。你需要上传你的数据库文件和模型的 pkl 文件。

这是本项目中最具创造性的部分了。所以如果你习惯使用 HTML、CSS 和 JavaScript，你可以让该应用程序越美观越好。

在原始文件中，你会发现网络应用程序已经能够正常工作并显示了可视化图表。你只用根据需要修改数据库和模型的文件路径。

还有一处地方你必须修改。我们提供了简单的数据可视化代码。你的任务是在网络应用程序中根据你从 SQLite 数据库中提取的数据再创建两个数据可视化图表。你可以修改和复制我们在原始文件中提供的代码来创建可视化图表。



# Github 和代码质量

在开发过程中，要将代码推 (push) 和提交 (commit) 到 Github 上，以保证没有重复工作，并且可以追踪你的修改过程。这还会让你的代码实现模块化，具有清晰的记录。保证包含有效的注释和文档字符串。这项软件工程实践会提高你以后在团队中工作时的沟通和合作能力。



## 原始代码

本项目的原始代码可以使用项目工作环境 IDE 填充完整。这是项目的文件结构：

```txt
- app
| - template
| |- master.html  # main page of web app
| |- go.html  # classification result page of web app
|- run.py  # Flask file that runs app

- data
|- disaster_categories.csv  # data to process 
|- disaster_messages.csv  # data to process
|- process_data.py
|- InsertDatabaseName.db   # database to save clean data to

- models
|- train_classifier.py
|- classifier.pkl  # saved model 

- README.md
```



# 在项目工作环境 IDE 中运行网络应用程序

在使用项目工作环境 IDE 时，这是找到 Flask app 的方法。

打开一个新的命令行窗口。你现在应该在工作环境文件夹，如果不是的话，使用命令行命令进入含有 run.py 文件的文件夹。

在命令行中输入：

```python
python run.py
```

如果没有报错，你的网络应用程序现在应该正常运行了。



现在打开另一个命令行窗口。

输入

```python
env|grep WORK
```

你会发现类似如下输出：



![img](https://video.udacity-data.com/topher/2018/February/5a8e41a1_screen-shot-2018-02-21-at-8.05.18-pm/screen-shot-2018-02-21-at-8.05.18-pm.png)



在一个新的网页浏览器窗口，进行如下输入：

```
https://SPACEID-3001.SPACEDOMAIN
```

在本例中，应该输入： "https://viewa7a4999b-3001.udacity-student-workspaces.com/" （不要输入这个，只是举个例子）。你的 SPACEID 应该不一样。

这时你应该能够看到网络应用程序了。数字 3001 表示你的网络应用程序的端口。确保网址中一部分是 3001。