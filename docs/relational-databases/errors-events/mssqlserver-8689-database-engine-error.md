---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: b087239a8daadf20c15374524b61cbcf7c468b38
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
  
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
  
