---
title: MSSQLSERVER_17066 | Microsoft Docs
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
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f366eb8fbb486f836b7cfc8f0d92ffb1b0fe5023
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070951"
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
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
