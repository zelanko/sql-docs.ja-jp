---
title: MSSQLSERVER_3456 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 129e1d8aa2725594871eaa48c2c983767eb46d73
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551557"
---
# <a name="mssqlserver_3456"></a>MSSQLSERVER_3456
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3456|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|REC_REDOLSNMISMATCH|  
|メッセージ テキスト|トランザクション ID %S_XID、ページ %S_PGID、データベース '%.*ls' (データベース ID %d) のログ レコード %S_LSN を再実行できませんでした。 ページ:LSN = %S_LSN、型 = %ld。 Log:OpCode = %ld、コンテキスト %ld、PrevPageLSN: %S_LSN。 データベースをバックアップから復元するか、データベースを修復してください。|  
  
## <a name="explanation"></a>説明  
 復元操作で、トランザクション ログを再実行できませんでした。 このエラーによって、データベースは SUSPECT 状態になっています。 プライマリ ファイル グループ、また場合によってはその他のファイル グループには、問題があり、損傷している可能性があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動中はデータベースを復旧できないため、データベースを使用できません。 問題を解決するには、ユーザーによる操作が必要です。  
  
 このエラーが **tempdb**で発生した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスはシャットダウンします。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーは、サーバー インスタンスの起動またはデータベースの復旧を試行したときのシステム上の一時的な状態が原因である可能性があります。 また、データベースを起動しようとするたびに発生する永続的なエラーが原因である可能性もあります。 原因の詳細については、Windows イベント ログで、具体的な問題点を示しているこれより前のエラーを調べてください。  
  
 このエラー 3456 の発生の原因については、Windows イベント ログをさかのぼって、具体的な問題点を示すエラーを調べてください。 ユーザーに求められる適切な対処は、Windows イベント ログが示している情報、つまり、その [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーが一時的な状態によって引き起こされたのか、永続的なエラーが原因で引き起こされたのかによって異なります。 エラー 3456 をトラブルシューティングするためのユーザー操作の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [データベースの全体復元 &#40;単純復旧モデル&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
