# Flask 应用在 Heroku 上的部署指南

本指南将帮助你将一个简单的 Flask 应用部署到 Heroku 平台上。以下是详细的步骤和说明。

## 目录

1. [准备工作](#准备工作)
2. [创建 Flask 应用](#创建-Flask-应用)
3. [配置 Heroku](#配置-Heroku)
4. [部署应用](#部署应用)
5. [常见问题](#常见问题)

## 准备工作

在开始之前，请确保你已经安装了以下工具：

- [Python](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)
- [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

## 创建 Flask 应用

1. **创建一个新的目录并进入该目录**

    ```bash
    mkdir myflaskapp
    cd myflaskapp
    ```

2. **创建虚拟环境并激活**

    ```bash
    python -m venv venv
    source venv/bin/activate  # 在 Windows 上使用 `venv\Scripts\activate`
    ```

3. **安装 Flask**

    ```bash
    pip install Flask
    ```

4. **创建应用文件**

    在项目根目录下创建一个名为 `app.py` 的文件，并添加以下内容：

    ```python
    from flask import Flask

    app = Flask(__name__)

    @app.route('/')
    def hello_world():
        return 'Hello, World!'

    if __name__ == '__main__':
        app.run(debug=True)
    ```

5. **创建 requirements.txt**

    ```bash
    pip freeze > requirements.txt
    ```

6. **创建 Procfile**

    在项目根目录下创建一个名为 `Procfile` 的文件，并添加以下内容：

    ```
    web: python app.py
    ```

7. **创建 runtime.txt**

    在项目根目录下创建一个名为 `runtime.txt` 的文件，并添加以下内容：

    ```
    python-3.9.6
    ```

## 配置 Heroku

1. **登录 Heroku**

    ```bash
    heroku login
    ```

2. **创建 Heroku 应用**

    ```bash
    heroku create
    ```

3. **初始化 Git 仓库**

    ```bash
    git init
    git add .
    git commit -m "Initial commit"
    ```

4. **关联 Heroku 远程仓库**

    ```bash
    heroku git:remote -a your-app-name
    ```

## 部署应用

1. **推送代码到 Heroku**

    ```bash
    git push heroku master
    ```

2. **打开应用**

    ```bash
    heroku open
    ```

## 常见问题

1. **如何查看日志？**

    ```bash
    heroku logs --tail
    ```

2. **如何更新应用？**

    在本地修改代码后，提交并推送到 Heroku：

    ```bash
    git add .
    git commit -m "Update app"
    git push heroku master
    ```

3. **如何设置环境变量？**

    例如，设置 Flask 的 `SECRET_KEY`：

    ```bash
    heroku config:set SECRET_KEY=your_secret_key
    ```

通过以上步骤，你应该能够成功将一个简单的 Flask 应用部署到 Heroku 上。如果在过程中遇到任何问题，请参考 Heroku 的官方文档或社区支持。
