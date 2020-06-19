---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 439d282f18490a4353d6528276eaf7e4231c503b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969802"
---
# <a name="mssqlserver_10535"></a>MSSQLSERVER_10535
    
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
 [sp_create_plan_guide_from_handle &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
