---
title: 複数データベースのクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: dd86d3e1c67cb1a87690919a6d9336a434d14954
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075084"
---
# <a name="cross-database-queries"></a>複数データベースにまたがるクエリ
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、メモリ最適化テーブルで複数データベースにまたがるトランザクションはサポートされません。 メモリ最適化テーブルにもアクセスする同じトランザクションまたは同じクエリから別のデータベースにアクセスすることはできません。 あるデータベースのテーブルから別のデータベースのメモリ最適化テーブルに、データを簡単にコピーすることはできません。  
  
 テーブル変数はトランザクション処理されません。 そのため、メモリ最適化テーブル変数を複数データベースにまたがるクエリで使用して、あるデータベースのデータを別のデータベースのメモリ最適化テーブルに簡単に移動できるようにすることができます。 2 つのトランザクションを使用できます。 最初のトランザクションで、リモート テーブルから変数にデータを挿入します。 2 つ目のトランザクションで、ローカルなメモリ最適化テーブルに変数からデータを挿入します。  
  
 例については、行をコピーする、データベース db1 のテーブル t1 から db2 の場合で、テーブル t2 に変数を使用して@v1型 dbo.tt1 のようなもの使用できます。  
  
```tsql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)  
  
  