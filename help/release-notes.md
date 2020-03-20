---
title: 新增功能? 发行说明——自动表单转换服务
description: '了解自动表单转换服务的最新功能和修复的错误 '
translation-type: tm+mt
source-git-commit: e88b9606878cb408c0369b5f20a644db93578f64

---


# 自动表单转换服务：发行说明

自动表单转换服务不断收到改进。 要了解最新动态，请定期访问本页。 本页为您提供了以下相关信息：

* 最新版本
* 新增功能
* 错误修复
* 已弃用的功能
* 特殊说明
* 更改的未来计划

本页面会按月更新，因此请定期重新访问它。

## 2020年3月20日(AFC-2020.03.1)

### 新增功能

**自动检测表单中的逻辑部分**

默认情况下，服务为输入PDF表单的每页创建单独的顶级面板。 现在，您可以选择 **[!UICONTROL Auto-detect logical sections]** 选项来删除为每个PDF页面创建单独的顶级面板并自动检测逻辑部分的概念。 将表单的服务俱乐部相关字段添加到逻辑部分。 例如，与帐单地址相关的所有字段都会被汇总到一个部分，而与发运地址相关的所有字段都会被汇总到另一个部分。 该服务还为每个自动检测到的逻辑部分创建单独的顶级面板。

### 改进功能

**列表检测方面的改进**

该服务现在在检测项目符号列表和编号列表方面更加有效。 它现在可以轻松检测多级列表。

### 特殊说明

**安装Automated Forms Conversion Service Connector包**

您需要连接器软件包1.1.38或更高版本才能使用AFC-2020.03.1版中提供的最新功能和改进。您可以从 [AEM包共享下载连接器包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN)。

如果您已经拥有运行中的自动表单转换服务环境，要使用转换服务的最新功能，请按上述顺序安装最新的服务包、最新的AEM Forms加载项包和最新的连接器包。 有关详细说明，请参阅 [配置自动表单转换服务文章](configure-service.md) 。
