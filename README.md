# Flask 应用在 Heroku 上的部署指南
本指南将帮助你将一个简单的 Flask 应用部署到 Heroku 平台上。以下是详细的步骤和说明。

目录
准备工作
创建 Flask 应用
配置 Heroku
部署应用
常见问题
准备工作
在开始之前，请确保你已经安装了以下工具：

Python
Git
Heroku CLI
创建 Flask 应用
创建一个新的目录并进入该目录

<BASH>
mkdir myflaskapp
cd myflaskapp
创建虚拟环境并激活

<BASH>
python -m venv venv
source venv/bin/activate  # 在 Windows 上使用 `venv\Scripts\activate`
安装 Flask

<BASH>
pip install Flask
创建应用文件

在项目根目录下创建一个名为 app.py 的文件，并添加以下内容：

<PYTHON>
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(debug=True)
创建 requirements.txt

<BASH>
pip freeze > requirements.txt
创建 Procfile

在项目根目录下创建一个名为 Procfile 的文件，并添加以下内容：

<TEXT>
web: python app.py
创建 runtime.txt

在项目根目录下创建一个名为 runtime.txt 的文件，并添加以下内容：

<TEXT>
python-3.9.6
配置 Heroku
登录 Heroku

<BASH>
heroku login
创建 Heroku 应用

<BASH>
heroku create
初始化 Git 仓库

<BASH>
git init
git add .
git commit -m "Initial commit"
关联 Heroku 远程仓库

<BASH>
heroku git:remote -a your-app-name
部署应用
推送代码到 Heroku

<BASH>
git push heroku master
打开应用

<BASH>
heroku open
常见问题
如何查看日志？

<BASH>
heroku logs --tail
如何更新应用？

在本地修改代码后，提交并推送到 Heroku：

<BASH>
git add .
git commit -m "Update app"
git push heroku master
如何设置环境变量？

例如，设置 Flask 的 SECRET_KEY：

<BASH>
heroku config:set SECRET_KEY=your_secret_key
通过以上步骤，你应该能够成功将一个简单的 Flask 应用部署到 Heroku 上。如果在过程中遇到任何问题，请参考 Heroku 的官方文档或社区支持。


