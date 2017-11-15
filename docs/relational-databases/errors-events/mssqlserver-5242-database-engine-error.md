---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 5cdf9006f511709715627c17c7ada22326c5e67f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5242|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|データベース '%.*ls'(ID:%d) のページ %S_PGID で内部操作中に、一貫性が損なわれていることが検出されました。 テクニカル サポートにお問い合わせください。 参照番号 %ld。|  
  
## <a name="explanation"></a>説明  
エラー メッセージで参照されているデータベース ページで構造の一貫性が損なわれています。  
  
## <a name="see-also"></a>参照  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[データベース ファイルとファイル グループ](~/relational-databases/databases/database-files-and-filegroups.md)  
  
