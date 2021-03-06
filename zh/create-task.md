---
title: 创建数据同步任务
summary: 了解 TiDB Data Migration 如何创建数据同步任务。
category: reference
---

# 创建数据同步任务

`start-task` 命令用于创建数据同步任务。当数据同步任务启动时，DM 将[自动对相应权限和配置进行前置检查](precheck.md)。

{{< copyable "" >}}

```bash
help start-task
```

```
start a task as defined in the config file

Usage:
 dmctl start-task [-s source ...] <config-file> [flags]

Flags:
 -h, --help   help for start-task

Global Flags:
 -s, --source strings   MySQL Source ID
```

## 命令用法示例

{{< copyable "" >}}

```bash
start-task [ -s "mysql-replica-01"] ./task.yaml
```

## 参数解释

+ `-s`：
    - 可选
    - 指定在特定的一个 MySQL 源上执行 `task.yaml`
    - 如果设置，则只启动指定任务在该 MySQL 源上的子任务
+ `config-file`：
    - 必选
    - 指定 `task.yaml` 的文件路径

## 返回结果示例

{{< copyable "" >}}

```bash
start-task task.yaml
```

```
{
    "result": true,
    "msg": "",
    "sources": [
        {
            "result": true,
            "msg": "",
            "source": "mysql-replica-01",
            "worker": "worker1"
        }
    ]
}
```
