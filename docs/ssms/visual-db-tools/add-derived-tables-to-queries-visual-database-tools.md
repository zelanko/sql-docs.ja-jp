---
title: クエリへの派生テーブルの追加
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: a234da70206c87387b38f55b64304f6ed8e31dc9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009337"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>クエリへの派生テーブルの追加 (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
派生テーブルは、クエリのソース テーブルとして使用される結果セットです。 **ダイアグラム ペイン**でクエリに派生テーブルを追加できます。  
  
### <a name="to-add-a-derived-table-to-a-query"></a>クエリに派生テーブルを追加するには  
  
1.  既存のクエリを開くか、新しいクエリを作成します。  
  
2.  **ダイアグラム ペイン** を右クリックし、 **[派生した新しいテーブルの追加]** を選択します。  
  
    derivedtbl_*N* という名前で新しいテーブルが追加され、派生テーブルの SELECT ステートメントがクエリの FROM 句に追加されます。  
  
## <a name="see-also"></a>参照  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[クエリを開く (Visual Database Tools)](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](https://msdn.microsoft.com/dc85caea-54d1-49af-b166-f3aa2f3a93d0)  
  
