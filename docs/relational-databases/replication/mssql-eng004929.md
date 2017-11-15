---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84c2b4d77277b2d63c652dc5c4f02625921e2f46
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|4929|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|%S_MSG '%.*ls' は、レプリケーションでパブリッシュされているので変更できません。|  
  
## <a name="explanation"></a>説明  
 通常、このエラーは、トランザクション レプリケーションでパブリッシュされているテーブル上の主キーの制約を削除しようとすると発生します。 トランザクション レプリケーションではパブリッシュされたテーブルごとに 1 つの主キーが必要であるため、制約は削除できません。  
  
## <a name="user-action"></a>ユーザーの操作  
 制約を削除するには、最初にテーブルに関連付けられているアーティクルを削除します。 詳細については、「[既存のパブリケーションでのアーティクルの追加および削除](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。 レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
