---
title: 新增功能? 发行说明——自动表单转换服务
description: '了解自动表单转换服务的最新功能和修复的错误 '
translation-type: tm+mt
source-git-commit: dc17dfcb331df6144b8a7ce3c9c9d840b1182a95

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

AFC-2020.03.1版本提供对该功能的早期访 **[!UICONTROL Auto-detect logical sections]** 问。

默认情况下，服务为PDF表单的每页创建单独的顶级面板。 现在，您可以使用该选 **[!UICONTROL Auto-detect logical sections]** 项拖放页面级面板（基于页码的面板）并仅创建逻辑面板。  它还会将不属于任何部分的字段归为俱乐部，前面有逻辑部分，而后面有跨两个相邻页面的逻辑部分的字段则归入单个逻辑部分。 例如，如果某个逻辑部分的某些字段位于第1页的末尾，而某些字段位于第2页的开头，则所有此类字段都会汇集到一个逻辑部分中。

您需要连接器包1.1.38或更高版本才能使用该 **[!UICONTROL Auto-detect logical sections]** 功能。 您可以从 [AEM包共享下载连接器包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1)。

### 改进功能

**列表检测的改进**

该服务现在在检测带项目符号和编号的列表方面更加有效。