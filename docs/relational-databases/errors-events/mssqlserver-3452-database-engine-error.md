---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df4e5faa901c840ebc1f03c828cb377edfad79ee
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3452|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|REC_CHECKIDENTITY|  
|メッセージ テキスト|データベース '%.*ls' (%d) の復旧でテーブル %d の ID 値の一貫性が損なわれているのを検出しました。 DBCC CHECKIDENT ('%.\*ls') を実行してください。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレード作業中に、データベース内の ID 値を復元するプロセスで、メタデータの不整合が検出されました。  
  
## <a name="user-action"></a>ユーザーの操作  
DBCC CHECKIDENT を実行します。  
  
