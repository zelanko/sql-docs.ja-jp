---
title: MSSQLSERVER_601 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2721158fd2f0e0803cd63306b13df01cc7ee9afa
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551144"
---
# <a name="mssqlserver_601"></a>MSSQLSERVER_601
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|601|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|データが移動されたので NOLOCK を使用したスキャンは続行できませんでした。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]が別のトランザクションによって更新または削除されたデータを読み取ろうとしているため、クエリの実行を続行できません。 このクエリでは、NOLOCK ロック ヒントまたは READ UNCOMMITTED トランザクション分離レベルのいずれかが使用されています。  
  
 通常、別のトランザクションによって変更されているデータへのアクセスは、データがロックされているために拒否されます。 しかし、NOLOCK ロック ヒントや READ UNCOMMITTED トランザクション分離レベルを使用すると、別のトランザクションによってロックされているデータをクエリで読み取ることができます。 まだコミットされておらず変更される可能性がある値を読み取ることができるため、この操作はダーティ リードと呼ばれます。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーが発生するとクエリは取り消されます。 クエリを再送信するか、NOLOCK ロック ヒントを削除します。  
  
## <a name="see-also"></a>参照  
 [MSSQLSERVER_605](mssqlserver-605-database-engine-error.md)   
 [テーブル ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
