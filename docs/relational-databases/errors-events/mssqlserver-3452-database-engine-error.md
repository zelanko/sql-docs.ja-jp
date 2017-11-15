---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 52865b3a6a4a036acafffa97cff5d0fbc6abbbf9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
  
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
  
