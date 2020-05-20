---
title: syscategories (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs:
- TSQL
helpviewer_keywords:
- syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fc4d6f55ca4e131abef21772911da923b854c81b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813904"
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、ジョブ、警告、オペレーターの分類に使用されるカテゴリを格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリの ID。|  
|**category_class**|**int**|カテゴリ内のアイテムの種類。<br /><br /> **1** = ジョブ<br /><br /> **2** = アラート<br /><br /> **3** = 演算子|  
|**category_type**|**tinyint**|カテゴリの種類:<br /><br /> **1** = ローカル<br /><br /> **2** = マルチサーバー<br /><br /> **3** = なし|  
|**name**|**sysname**|カテゴリの名前。|  
  
  
