---
title: 新增功能? 发行说明——自动表单转换服务
description: '了解自动表单转换服务的最新功能和修复的错误 '
translation-type: tm+mt
source-git-commit: c0ca850a0a1e82e34364766601011d6367b218ac

---


# 自动表单转换服务：发行说明

自动表单转换服务不断收到改进。 要了解最新动态，请定期访问本页。 本页为您提供了以下相关信息：

* 早期访问
* 最新版本
* 新增功能
* 改进
* 错误修复
* 已弃用的功能
* 特殊说明
* 将来的更改计划

## 2020年3月20日(AFC-2020.03.1)

### 早期访问

**自动检测表单中的逻辑部分**

默认情况下，服务为PDF表单的每页创建单独的顶级面板。 现在，您可以使用该选 **[!UICONTROL Auto-detect logical sections]** 项来放置页面级面板（基于页码的面板）并仅创建逻辑面板。 它还将不属于具有前面逻辑部分的任何部分的字段和跨两个相邻页面的逻辑部分的字段限制为单个逻辑部分。 例如，如果某个逻辑部分的某些字段位于第1页的末尾，而某些字段位于第2页的开头，则所有此类字段都会汇集到一个逻辑部分中。

### 改进功能

**列表检测的改进**

该服务现在在检测带项目符号和编号的列表方面更加有效。

### 特殊说明

**安装Automated Forms Conversion Service Connector包**

您需要连接器软件包1.1.38或更高版本才能使用AFC-2020.03.1版中提供的最新功能和改进。您可以从 [AEM包共享下载连接器包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1)。

如果您已安装并运行Automated Forms Conversion服务环境，则要使用转换服务的最新功能，请按上述顺序安装最新的服务包、最新的AEM Forms Add-on包和最新的连接器包。 有关详细说明，请参阅 [配置自动表单转换服务文章](configure-service.md) 。