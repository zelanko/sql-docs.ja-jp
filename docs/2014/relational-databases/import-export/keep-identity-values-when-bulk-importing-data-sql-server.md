---
title: データの一括インポート時の ID 値の保持 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5bb2fbd3129475c5d712cd4d1fce8bbe29ea096f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011907"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a>データの一括インポート時の ID 値の保持 (SQL Server)
  Id 値を含むデータファイルは、の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに一括インポートできます。 既定では、インポートされたデータ ファイルの ID 列の値は無視され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって固有の値が自動的に割り当てられます。 固有の値は、テーブル作成時に指定されたシード値と増分値に基づいています。  
  
 データ ファイルにテーブルの ID 列の値が含まれていない場合は、フォーマット ファイルを使用してデータをインポートするときにテーブルの ID 列をスキップするように指定します。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は固有の値をこの列に自動的に割り当てます。  
  
 テーブルにデータ行を一括インポートするときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が ID 値を割り当てないようにするには、適切な keep-identity コマンド修飾子を使用します。 keep-identity 修飾子を指定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではデータ ファイルの ID 値を使用します。 このような修飾子は次のとおりです。  
  
|command|Keep-identity 修飾子|修飾子の種類|  
|-------------|------------------------------|--------------------|  
|`bcp`|**-E**|スイッチ|  
|BULK INSERT|KEEPIDENTITY|引数|  
|INSERT ...SELECT * FROM OPENROWSET(BULK...)|KEEPIDENTITY|テーブル ヒント|  
  
 詳細については、「[bcp Utility](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」、「[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)」、「[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)」、「[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)」を参照してください。  
  
> [!NOTE]  
>  複数のテーブルで使用できる自動的に増分する番号、またはテーブルを参照せずにアプリケーションから呼び出すことができる自動的に増分する番号を作成するには、「[シーケンス番号](../sequence-numbers/sequence-numbers.md)」を参照してください。  
  
## <a name="examples"></a>例  
 このトピックの例では、INSERT ... SELECT * FROM OPENROWSET(BULK...) を使用し、既定値を維持して、データを一括インポートします。  
  
### <a name="sample-table"></a>サンプル テーブル  
 この一括インポートの例では、**dbo** スキーマの下にある **AdventureWorks** サンプル データベースで **myTestKeepNulls** というテーブルを作成する必要があります。 このテーブルを作成するには 
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 
  ** の基になる **Department`myDepartment` テーブルには IDENTITY_INSERT があり、OFF に設定されています。 したがって、ID 列にデータをインポートするには、KEEPIDENTITY または **-E** を指定する必要があります。  
  
### <a name="sample-data-file"></a>サンプル データ ファイル  
 一括インポートの例で使用したデータ ファイルには、ネイティブ形式で `HumanResources.Department` テーブルから一括エクスポートされたデータが含まれています。 このデータ ファイルを作成するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコマンド プロンプトで次のように入力します。  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a>サンプル フォーマット ファイル  
 この一括インポートの例では `myDepartment-f-x-n.Xml` という XML フォーマット ファイルを使用します。ここではネイティブのデータ形式が使用されています。 この例では、`bcp` を使用して、`HumanResources.Department` データベースの `AdventureWorks` テーブルからこのフォーマット ファイルを作成します。 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 フォーマット ファイルの作成方法の詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a>A. bcp を使用して ID 値を保持する方法  
 次の例では、`bcp` を使用してデータを一括インポートするときに ID 値を保持する方法について説明します。 
  `bcp` コマンドは、フォーマット ファイル `myDepartment-f-n-x.Xml` を使用し、次のスイッチを含んでいます。  
  
|修飾子|[説明]|  
|----------------|-----------------|  
|**-E**|データ ファイルの ID 値を ID 列に使用するように指定します。|  
|**-T**|ユーティリティが`bcp`信頼関係接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用してに接続するように指定します。|  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a>B. BULK INSERT を使用して ID 値を保持する方法  
 次の例では、BULK INSERT を使用して、`myDepartment-c.Dat` ファイルから `AdventureWorks.HumanResources.myDepartment` テーブルにデータを一括インポートします。 このステートメントは、`myDepartment-f-n-x.Xml` フォーマット ファイルを使用し、データ ファイル内の任意の ID 値が必ず保持されるように KEEPIDENTITY オプションを含んでいます。  
  
 
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のように実行します。  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a>C. OPENROWSET を使用して ID 値を保持する方法  
 次の例では、OPENROWSET 一括行セット プロバイダーを使用して、`myDepartment-c.Dat` ファイルから `AdventureWorks.HumanResources.myDepartment` テーブルにデータを一括インポートします。 このステートメントは、`myDepartment-f-n-x.Xml` フォーマット ファイルを使用し、データ ファイル内の任意の ID 値が必ず保持されるように KEEPIDENTITY ヒントを含んでいます。  
  
 
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のように実行します。  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [一括インポート中に Null を保持するか、既定値を使用 &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **フォーマットファイルを使用するには**  
  
-   [フォーマットファイル &#40;SQL Server を作成し&#41;](create-a-format-file-sql-server.md)  
  
-   [フォーマットファイルを使用して SQL Server &#40;データを一括インポートする&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [フォーマットファイルを使用して、テーブル列をデータファイルフィールド &#40;SQL Server にマップ&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [フォーマットファイルを使用して、データフィールド &#40;SQL Server をスキップし&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [フォーマットファイルを使用してテーブル列をスキップする &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **一括インポートまたは一括エクスポートのデータ形式を使用するには**  
  
-   [以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [文字形式を使用してデータをインポートまたはエクスポート &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用してデータをインポートまたはエクスポート &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用してデータをインポートまたはエクスポート &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用してデータをインポートまたはエクスポート &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Bcp を使用して互換性のためのデータ形式を指定するには**  
  
1.  [SQL Server &#40;のフィールドターミネータと行ターミネータを指定し&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Bcp &#40;SQL Server を使用したデータファイルのプレフィックス長の指定&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Bcp &#40;SQL Server を使用して File Storage の種類を指定し&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;のバックアップ &#40;](/sql/t-sql/statements/backup-transact-sql)   
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Transact-sql&#41;&#40;テーブルヒント](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
