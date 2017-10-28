---
title: "インベントリ スキーマ (AccessToSQL) にアクセス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- columns table
- databases table
- exported metadata
- exporting, schemas of exported metadata
- foreign keys table
- forms table
- indexes, table
- inventory schemas
- macros table
- modules table
- queries table
- reference, inventory schemas
- reports table
- schemas of exported metadata
- schemas, exported metadata
- SSMA_Access_InventoryColumns
- SSMA_Access_InventoryDatabases
- SSMA_Access_InventoryForeignKeys
- SSMA_Access_InventoryForms
- SSMA_Access_InventoryIndexes
- SSMA_Access_InventoryMacros
- SSMA_Access_InventoryModules
- SSMA_Access_InventoryQueries
- SSMA_Access_InventoryReports
- SSMA_Access_InventoryTables
- tables, inventory
ms.assetid: fdd3cff2-4d62-4395-8acf-71ea8f17f524
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cd7d907f2c78125a477737299f6aaee28b5ccc7f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="access-inventory-schemas-accesstosql"></a>アクセスのインベントリ スキーマ (AccessToSQL)
次のセクションへのアクセスのスキーマをエクスポートするときに、SSMA によって作成されるテーブルを記述する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
## <a name="databases"></a>データベース  
データベースのメタデータをエクスポート、 **SSMA_Access_InventoryDatabases**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|各データベースを一意に識別する GUID です。 この列は、テーブルの主キーもです。|  
|**DatabaseName**|**nvarchar (4000)**|Access データベースの名前。|  
|**ExportTime**|**datetime**|このメタデータが SSMA によって作成された日付と時刻。|  
|**ファイル パス**|**nvarchar (4000)**|Access データベースの完全パスとファイル名。|  
|**ファイル サイズ**|**bigint**|Access データベース (KB 単位) のサイズ。|  
|**FileOwner**|**nvarchar (4000)**|Access データベースの所有者として指定されている Windows アカウント。|  
|**作成日時**|**datetime**|日付と Access データベースが作成された時刻。|  
|**DateModified**|**datetime**|日付と Access データベースの最終変更時刻。|  
|**TablesCount**|**int**|Access データベース内のテーブルの数。|  
|**QueriesCount**|**int**|Access データベース内のクエリの数。|  
|**FormsCount**|**int**|Access データベース内のフォームの数。|  
|**ModulesCount**|**int**|Access データベース内のモジュールの数。|  
|**ReportsCount**|**int**|Access データベース内のレポートの数。|  
|**MacrosCount**|**int**|Access データベース内のマクロの数。|  
|**AccessVersion**|**nvarchar (4000)**|データベースのアクセス バージョンです。|  
|**[照合順序]**|**nvarchar (4000)**|Access データベースの照合順序です。 照合順序は、データベースの並べ替えし、文字列を比較する方法を決定します。|  
|**JetVersion**|**nvarchar (4000)**|Jet データベース エンジンのバージョン。 Access データベースは、基になる Jet データベース エンジンを使用します。|  
|**IsUpdatable**|**bit**|データベースを更新できるかどうかを示します。 値が 1 の場合は、データベースは更新可能です。 値が 0 の場合、データベースは読み取り専用です。|  
|**QueryTimeout**|**int**|構成されている ODBC クエリのタイムアウト値 (秒) のデータベースです。 既定値は 60 秒です。|  
  
## <a name="tables"></a>テーブル  
テーブルのメタデータをエクスポート、 **SSMA_Access_InventoryTables**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|このテーブルを含むデータベースを識別します。|  
|**TableId**|**uniqueidentifier**|テーブルを一意に識別する GUID です。 この列は、テーブルの主キーもです。|  
|**テーブル名**|**nvarchar (4000)**|テーブルの名前です。|  
|**RowsCount**|**int**|テーブルに含まれる行数です。|  
|**ValidationRule**|**nvarchar (4000)**|テーブルの有効な入力を定義するルール。 検証規則が存在しない場合、このフィールドは空の文字列を含めます。|  
|**LinkedTable**|**nvarchar (4000)**|別のテーブル、存在する場合、テーブルにリンクされています。 このテーブルを使用して、追加、削除、およびその他のテーブルを更新するをテーブルをリンクできます。|  
|**ExternalSource**|**nvarchar (4000)**|データ ソースに存在する場合に関連付けられているテーブル。 テーブルがリンクされている場合、このフィールドで指定された外部データ ソースがあります。|  
  
## <a name="columns"></a>列  
列のメタデータをエクスポート、 **SSMA_Access_InventoryColumns**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|この列を含むデータベースを識別します。|  
|**TableId**|**uniqueidentifier**|この列を含むテーブルを識別します。|  
|**ColumnId**|**int**|インクリメント整数列を識別します。 **ColumnId**テーブルの主キーします。|  
|**[ColumnName]**|**nvarchar (4000)**|列の名前です。|  
|**IsNullable**|**bit**|列が null 値を含めることができるかどうかを指定します。 値が 1 の場合は、列は null 値を含めることができます。 値が 0 の場合、列は null 値を含めることはできません。 検証規則は null 値を防ぐためにも使用できますに注意してください。|  
|**DataType**|**nvarchar (4000)**|など、列のデータ アクセス種類**テキスト**または**長い**です。|  
|**IsAutoIncrement**|**bit**|列が整数値を自動的にインクリメントするかどうかを指定します。 値が 1 の場合は、整数が自動インクリメントします。|  
|**序数**|**smallint**|0 から始まる、テーブル内の列の順序。|  
|**DefaultValue**|**nvarchar (4000)**|列の既定値。|  
|**ValidationRule**|**nvarchar (4000)**|データを追加または列の更新の検証に使用される規則です。|  
  
## <a name="indexes"></a>インデックス  
インデックスのメタデータをエクスポート、 **SSMA_Access_InventoryIndexes**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|このインデックスを含むデータベースを識別します。|  
|**TableId**|**uniqueidentifier**|このインデックスを含むテーブルを識別します。|  
|**IndexId**|**int**|インクリメントを整数インデックスを識別します。 この列は、テーブルの主キーです。|  
|**IndexName**|**nvarchar (4000)**|インデックスの名前。|  
|**ColumnsIncluded**|**nvarchar (4000)**|インデックスに含まれている列を一覧表示します。 列名は、セミコロンで区切られます。|  
|**IsUnique**|**bit**|かどうか、インデックス内の各項目が一意である必要がありますを指定します。 複数列インデックスの値の組み合わせは一意である必要があります。 値が 1 の場合は、インデックスは一意の値を適用します。|  
|**IsPK**|**bit**|インデックスが主キーの定義の一部として自動的に作成されたかどうかを指定します。|  
|**IsClustered**|**bit**|インデックスがクラスター化されているかどうかを指定します。 クラスター化インデックスでは、データの物理的な記憶域を並べ替えます。 テーブルには、1 つだけのクラスター化インデックスを持つことができます。|  
  
## <a name="foreign-keys"></a>外部キー  
外部キーのメタデータをエクスポート、 **SSMA_Access_InventoryForeignKeys**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|この外部キーを含むデータベースを識別します。|  
|**TableId**|**uniqueidentifier**|この外部キーを含むテーブルを識別します。|  
|**ForeignKeyId**|**int**|外部キーを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**ForeignKeyName**|**nvarchar (4000)**|インデックスの名前。|  
|**ReferencedTableId**|**uniqueidentifier**|ソース列を含むテーブルを識別します。|  
|**SourceColumns**|**nvarchar (4000)**|外部キー列または列を一覧表示します。|  
|**ReferencedColumns**|**nvarchar (4000)**|主キー列または外部キーによって参照されている列を一覧表示します。|  
|**IsCascadeForUpdate**|**bit**|主キーの値が更新された場合、そのキー値を参照するすべての行も更新を指定します。|  
|**IsCascadeForDelete**|**bit**|主キーの値が削除された場合、そのキー値を参照するすべての行も削除されたことを指定します。|  
|**IsEnforced**|**bit**|外部キー制約が適用されているを指定します。|  
  
## <a name="queries"></a>クエリ  
クエリのメタデータをエクスポート、 **SSMA_Access_InventoryQueries**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|このクエリを含むデータベースを識別します。|  
|**QueryId**|**int**|クエリを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**QueryName**|**nvarchar (4000)**|クエリの名前。|  
|**QueryText**|**nvarchar (4000)**|SELECT ステートメントなどの SQL クエリ コード。|  
|**IsUpdateable**|**bit**|かどうか、クエリは更新可能または読み取り専用を指定します。|  
|**QueryType**|**nvarchar (4000)**|など、クエリの種類を指定**選択**または**SetOperation**です。|  
|**ExternalSource**|**nvarchar (4000)**|クエリでは、外部データ ソースを参照する場合、クエリで使用される接続文字列です。|  
  
## <a name="forms"></a>フォーム  
形式のメタデータをエクスポート、 **SSMA_Access_InventoryForms**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|このフォームが含まれるデータベースを識別します。|  
|**FormId**|**int**|フォームを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**フォーム名**|**nvarchar (4000)**|フォームの名前。|  
  
## <a name="macros"></a>マクロ  
マクロのメタデータをエクスポート、 **SSMA_Access_InventoryMacros**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|マクロが含まれるデータベースを識別します。|  
|**MacroId**|**int**|マクロを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**マクロ名**|**nvarchar (4000)**|マクロの名前。|  
  
## <a name="reports"></a>レポート  
レポートのメタデータをエクスポート、 **SSMA_Access_InventoryReports**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|レポートを含むデータベースを識別します。|  
|**ReportId**|**int**|レポートを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**ReportName**|**nvarchar (4000)**|レポートの名前です。|  
  
## <a name="modules"></a>モジュール  
モジュールのメタデータをエクスポート、 **SSMA_Access_InventoryModules**テーブル。 このテーブルには、次の列が含まれています。  
  
|列名|データ型|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|モジュールを含むデータベースを識別します。|  
|**ModuleId**|**int**|モジュールを識別する増分する整数。 この列は、テーブルの主キーです。|  
|**ModuleName**|**nvarchar (4000)**|モジュールの名前。|  
  
## <a name="see-also"></a>参照  
[アクセスのインベントリをエクスポートします。](http://msdn.microsoft.com/en-us/7e1941fb-3d14-4265-aff6-c77a4026d0ed)  
  

