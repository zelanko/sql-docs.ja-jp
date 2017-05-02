---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ffb2635978477bdd04c52bfa0fae32156ad0c50d
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver17066"></a>MSSQLSERVER_17066
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17066|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLASSERT_ONLY|  
|メッセージ テキスト|SQL Server アサーション: ファイル: \<%s>、行 = %d 失敗したアサーション = '%s'。 このエラーはタイミングに関係している可能性があります。 ステートメントの再実行後もエラーが解決しない場合は、DBCC CHECKDB を使用してデータベースの構造上の整合性を確認するか、またはサーバーを再起動してインメモリ データ構造体が壊れていないことを確認してください。|  
  
## <a name="explanation"></a>説明  
このエラーは、一時的なタイミングに関係する問題や、メモリ内またはディスク上のデータの破損によって発生する可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
例外を発生させたステートメントを再実行します。 タイミングに関係しているイベントによって発生したエラーの場合、エラーは再び発生しません。 問題が引き続き発生する場合は、DBCC CHECKDB を実行してディスク上の破損を確認します。 サーバーを再起動し、インメモリ データ構造体が壊れていないことを確認します。  
  
## <a name="see-also"></a>参照  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  

