---
title: dbo.sys通知 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysnotifications_TSQL
- sysnotifications
- sysnotifications_TSQL
- dbo.sysnotifications
dev_langs:
- TSQL
helpviewer_keywords:
- sysnotifications system table
ms.assetid: c5150d18-e8b7-48a7-ada7-77c583af6e41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b6ac4c1c037c186e1fe6fc20ad1b3ef0cfba976
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890423"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sys通知 (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  通知ごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|警告の ID。|  
|**operator_id**|**int**|通知を送信するオペレーターの ID。|  
|**notification_method**|**tinyint**|通知の方法。<br /><br /> **1** = 電子メール<br /><br /> **2** = ポケットベル<br /><br /> **4**  = **netsend**<br /><br /> **7** = すべて|  
  
  
