---
layout: default
title:  "一个轻量、简洁的PHP Csv导出类"
date:   2021-06-29 13:43:50 +0800
categories: projects
excerpt_separator: <!--more-->
---
### [项目地址](https://github.com/XihongKe/CsvExporter)
### 安装
```bash
composer require xihongke/csv-exporter
```
<!--more-->
### 用法
```php
use XihongKe\CsvExporter\CsvExporter;

$exporter = new CsvExporter("学生列表", ['学号', '姓名', '性别']);

// 往表里写入单行数据
$exporter->row(['1001', '张三', '男']);
// 多行数据
$exporter->rows([
    ['1002', '李红', '女'],
    ['1003', '吴均', '男'],
]);
```
