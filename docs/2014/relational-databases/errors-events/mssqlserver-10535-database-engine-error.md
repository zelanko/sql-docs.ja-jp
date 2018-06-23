---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ff4797fdd9d206ca459bc84facccfc588aafba00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174492"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10535|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_PLAN|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。指定されたプラン ハンドルに対応するプラン キャッシュでプランが見つかりませんでした。 キャッシュされたプラン ハンドルを指定します。 キャッシュされたプラン ハンドルの一覧を取得するには、sys.dm_exec_query_stats 動的管理ビューに対してクエリを実行します。|  
  
## <a name="explanation"></a>説明  
 指定されたプラン ハンドルに対応するプラン キャッシュ内にプランが見つかりませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 キャッシュされたプラン ハンドルを指定します。 キャッシュされたプラン ハンドルの一覧を取得するには、sys.dm_exec_query_stats 動的管理ビューに対してクエリを実行します。  
  
## <a name="see-also"></a>参照  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
