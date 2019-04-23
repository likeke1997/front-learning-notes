# 简介

pip（package installer for Python）is a command line program. When you install pip, a pip command is added to your system, which can be run from the command prompt. 

pip supports installing from PyPI, version control, local projects, and directly from distribution files pypi（python package index）is a repository of software for the Python programming language.

# 使用

```bash
python get-pip.py # 安装pip
pip install -U pip # 升级pip
pip install <somepackage> # 安装包
pip install <wheel> # 安装包
pip install -r requirements.txt # 批量安装包
pip uninstall somepackage # 卸载包
pip show somepackage # 显示包的详细信息
pip list # 显示已安装包的列表
pip list --outdated # 显示过期的包
```

# pip-review

```bash
pip install pip-review # 安装pip-review
pip-review --local --interactive # 批量更新过期的包
```

# 参考
+ [官网](https://pypi.org/project/pip/)
+ [官方文档](https://pip.pypa.io/en/stable/installing/)