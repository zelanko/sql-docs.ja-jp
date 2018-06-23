---
title: 同期 (レプリケーション TRANSACT-SQL プログラミング) 中にトリガーと制約の動作を制御 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 35
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e287beff3addbea618e825ef3b0664d9d005e7ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076863"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a>同期中にトリガーと制約の動作を制御する (レプリケーション Transact-SQL プログラミング)
  同期中、レプリケートされるテーブルでは、[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)、[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)、[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) の各ステートメントがレプリケーション エージェントによって実行され、これらのテーブルに対して設定されていたデータ操作言語 (DML) のトリガーが実行されます。 同期中はこれらのトリガーが起動しないようにしたり、制約が適用されないようにすることが必要になる場合があります。 このときの動作は、トリガーまたは制約がどのように作成されたかによって異なります。  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>同期中にトリガーが実行されないようにするには  
  
1.  新しいトリガーを作成する場合は、[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) の NOT FOR REPLICATION オプションを指定します。  
  
2.  既存のトリガーの場合は、[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) の NOT FOR REPLICATION オプションを指定します。  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>同期中に制約が適用されないようにするには  
  
1.  CHECK 制約または FOREIGN KEY 制約を新たに作成する場合は、 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) の制約定義で、CHECK NOT FOR REPLICATION オプションを指定します。  
  
## <a name="see-also"></a>参照  
 [テーブルの作成 &#40;データベース エンジン&#41;](../tables/create-tables-database-engine.md)  
  
  
