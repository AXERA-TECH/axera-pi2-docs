# AXera-Pi 2 User Manual

[Web Preview](https://axera-pi-2-docs-cn.readthedocs.io/zh-cn/latest/index.html)

## 1. 项目背景

**爱芯派2** (AXera-Pi 2) 开发板使用手册开源维护项目

- 提供 爱芯派2 使用文档和示例
- 促进社区开发人员共同维护文档。

## 2. 本地编译指南

### 2.1 git clone

```bash
git clone https://github.com/AXERA-TECH/axera-pi2-docs.git
```

目录如下:

```bash
.
├── LICENSE
├── Makefile
├── README.md
├── build
├── requirements.txt
└── source
    ├── conf.py
    ├── doc_appendix.md
    ├── doc_guide_advanced.md
    ├── doc_guide_quick_start.md
    ├── doc_introduction.md
    ├── doc_update_info.md
    ├── index.rst
    └── media
```

### 2.2 编译

安装依赖

```bash
pip install -r requirements.txt
```

在项目根目录下执行以下命令

```bash
$ make clean
$ make html
```

### 2.3 本地预览

编译后，使用浏览器查看它 `build/html/index.html`

## 3. 参考设计

这个项目是基于Sphinx，更多关于Sphinx的信息可以在这里找到 https://www.sphinx-doc.org/en/master/

## 4. 在线发布

基于 [ReadtheDocs](https://readthedocs.org/) 平台代理在线 Web 服务。
