---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bde8c78bcece74c17820bb11390c048355e4d5a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8689|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_DB|  
|メッセージ テキスト|USE PLAN ヒントで指定されたデータベース '%.*ls' は存在しません。 既存のデータベースを指定してください。|  
  
## <a name="explanation"></a>説明  
USE PLAN ヒントで指定したデータベースが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
USE PLAN ヒントで指定したすべてのデータベースが存在することを確認します。  
  
## <a name="see-also"></a>参照  
[クエリ ヒント &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
  
