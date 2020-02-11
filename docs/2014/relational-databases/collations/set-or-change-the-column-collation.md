---
title: 列の照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a16794bb2cd61829058d9fac7be11438f563d44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62918971"
---
# <a name="set-or-change-the-column-collation"></a>列の照合順序の設定または変更
  
  `char` 型、`varchar` 型、`text` 型、`nchar` 型、`nvarchar` 型、および `ntext` 型のデータのデータベース照合順序は、テーブルの列ごとに異なる照合順序を指定し、次のいずれかを使用することでオーバーライドできます。  
  
-   
  [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) と [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)の COLLATE 句。 次に例を示します。  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 詳細については、「 [照合順序と Unicode のサポート](collation-and-unicode-support.md)」を参照してください。  
  
-   管理オブジェクト`Column.Collation` (SMO [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) でプロパティを使用します。  
  
 次のいずれかから現在参照されている列は、照合順序を変更することはできません。  
  
-   計算列  
  
-   インデックス  
  
-   自動的に生成された、または CREATE STATISTICS ステートメントによって生成された分布統計情報  
  
-   CHECK 制約  
  
-   FOREIGN KEY 制約  
  
 
  **tempdb**を操作する場合、 [COLLATE](/sql/t-sql/statements/collations) 句に *database_default* オプションを指定することで、一時テーブルの列で、接続の現在のユーザー データベースでの既定の照合順序を **tempdb**の照合順序の代わりに使用するように指定することもできます。  
  
## <a name="collations-and-text-columns"></a>照合順序と text 列  
 データベースの既定の照合順序のコード ページと異なる照合順序が設定された `text` 列では、値の挿入と更新が可能です。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、値がこの列の照合順序に暗黙的に変換されます。  
  
## <a name="collations-and-tempdb"></a>照合順序と tempdb  
 
  **tempdb** データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動されるたびに作成され、 **model** データベースと同じ既定の照合順序が設定されます。 これは、通常、インスタンスの既定の照合順序と同じになります。 ユーザー データベースを作成して、 **model**と異なる既定の照合順序を指定すると、そのユーザー データベースでは **tempdb**と異なる既定の照合順序が使用されます。 一時ストアド プロシージャや一時テーブルは、すべて **tempdb**内に作成および格納されます。 その結果、一時テーブル内のすべての暗黙の列、および一時ストアド プロシージャ内で強制的に適用されるすべての既定の定数、変数、パラメーターでは、パーマネント テーブルやストアド プロシージャで作成される同等のオブジェクトとは異なる照合順序が指定されます。  
  
 このため、ユーザー定義データベースとシステム データベース オブジェクトの照合順序の不一致による問題が発生する可能性があります。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでは照合順序として Latin1_General_CS_AS が使用されていて、次のステートメントを実行するとします。  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 このシステムでは、 **tempdb** データベースにコード ページ 1252 の Latin1_General_CS_AS 照合順序が使用され、 `TestDB` と `TestPermTab.Col1` にコード ページ 1257 の `Estonian_CS_AS` 照合順序が使用されることになります。 次に例を示します。  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 上記の例では、 **tempdb** データベースで Latin1_General_CS_AS 照合順序が使用され、 `TestDB` と `TestTab.Col1` では `Estonian_CS_AS` 照合順序が使用されます。 次に例を示します。  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 
  **tempdb** ではサーバーの既定照合順序が使用され、 `TestPermTab.Col1` では異なる照合順序が使用されるので、"Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation. " (equal to 操作の 'Latin1_General_CI_AS_KS_WS' と 'Estonian_CS_AS' 間での照合順序の競合を解決できません。) というエラーが SQL Server から返されます。  
  
 このエラーを回避するには、次のいずれかを行います。  
  
-   一時テーブル列で、 **tempdb**ではなく、ユーザー データベースの既定の照合順序を使用するように指定します。 この措置によって、システムで必要とされる場合に、一時テーブルを複数のデータベース内で同様の形式が設定されたテーブルと併用できます。  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   次のように、 `#TestTempTab` 列に正しい照合順序を指定します。  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>参照  
 [サーバーの照合順序を設定または変更する](set-or-change-the-server-collation.md)   
 [データベースの照合順序の設定または変更](set-or-change-the-database-collation.md)   
 [Collation and Unicode Support](collation-and-unicode-support.md)  
  
  
