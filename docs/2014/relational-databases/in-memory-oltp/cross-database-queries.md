---
title: 複数データベースのクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b86fb120d8263ae48bb9a4e874e4cf0d012bf7a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050212"
---
# <a name="cross-database-queries"></a>複数データベースにまたがるクエリ
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、メモリ最適化テーブルで複数データベースにまたがるトランザクションはサポートされません。 メモリ最適化テーブルにもアクセスする同じトランザクションまたは同じクエリから別のデータベースにアクセスすることはできません。 あるデータベースのテーブルから別のデータベースのメモリ最適化テーブルに、データを簡単にコピーすることはできません。  
  
 テーブル変数はトランザクション処理されません。 そのため、メモリ最適化テーブル変数を複数データベースにまたがるクエリで使用して、あるデータベースのデータを別のデータベースのメモリ最適化テーブルに簡単に移動できるようにすることができます。 2 つのトランザクションを使用できます。 最初のトランザクションで、リモート テーブルから変数にデータを挿入します。 2 つ目のトランザクションで、ローカルなメモリ最適化テーブルに変数からデータを挿入します。  
  
 たとえば、dbo.tt1 型の変数を使用して、データベース db1 のテーブル t1 から db2 のテーブル t2 に行をコピーするに @v1 は、次のようなコードを使用できます。  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)  
  
  
