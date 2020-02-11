---
title: SchemaEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SchemaEnum
helpviewer_keywords:
- SchemaEnum enumeration [ADO]
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c064120e3c658cafd88a96953ff00e18fbaa9b88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931118"
---
# <a name="schemaenum"></a>SchemaEnum
[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドによって取得されるスキーマ**レコードセット**の種類を指定します。  
  
## <a name="remarks"></a>解説  
 各 ADO 定数に対して返される関数と列に関する追加情報については、 [「付録 B:](https://msdn.microsoft.com/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) OLE DB プログラマーリファレンスのスキーマ行セット」のトピックを参照してください。 各トピックの名前は、次の表の説明セクションにかっこで囲まれています。  
  
 ADO MD 定数ごとに返される関数と列に関する追加情報については、オンライン分析処理 (OLAP) のドキュメントの OLE DB の「 [Olap オブジェクトおよびスキーマ行セットの OLE DB](https://msdn.microsoft.com/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) 」のトピックを参照してください。 各トピックの名前は、次の表の説明列にかっこで囲まれています。  
  
 ADO [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)トピックの Description 列を参照して、OLE DB ドキュメント内の列のデータ型を ado データ型に変換できます。 たとえば、 **DBTYPE_WSTR**の OLE DB データ型は、 **ADWCHAR**の ADO データ型に相当します。  
  
 ADO では、定数、 **Adschemadbina キーワード**、および**adschemadbinを**使用したスキーマのような結果が生成されます。 ADO は**レコードセット**を作成し、各行に、 **IDBInfo:: Getkeywords**メソッドと**IDBInfo:: GetLiteralInfo**メソッドによって返された値を格納します。 これらのメソッドに関する追加情報については、OLE DB プログラマーリファレンス』の「 [IDBInfo](https://msdn.microsoft.com/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) 」セクションを参照してください。  
  
|常時|値|[説明]|制約列|  
|--------------|-----------|-----------------|------------------------|  
|**adSchemaAsserts**|0|特定のユーザーが所有する、カタログで定義されているアサーションを返します。<br /><br /> (アサーション行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCatalogs**|1 で保護されたプロセスとして起動されました|DBMS からアクセスできるカタログに関連付けられている物理属性を返します。<br /><br /> (カタログ行セット)|CATALOG_NAME|  
|**adSchemaCharacterSets**|2|指定したユーザーがアクセスできる、カタログで定義されている文字セットを返します。<br /><br /> (CHARACTER_SETS 行セット)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adSchemaCheckConstraints**|5|特定のユーザーが所有する、カタログに定義されている check 制約を返します。<br /><br /> (CHECK_CONSTRAINTS)セット|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCollations**|3|指定したユーザーがアクセスできる、カタログで定義されている文字の照合順序を返します。<br /><br /> (照合順序行セット)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adSchemaColumnPrivileges**|13|特定のユーザーが使用できる、または特定のユーザーによって許可される、カタログで定義されているテーブルの列に対する権限を返します。<br /><br /> (COLUMN_PRIVILEGES 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME、GRANTOR、GRANTEE|  
|**adSchemaColumns**|4|指定したユーザーがアクセスできる、カタログに定義されているテーブル (ビューを含む) の列を返します。<br /><br /> (COLUMNS 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME|  
|**adSchemaColumnsDomainUsage**|11|カタログで定義されている列のうち、カタログで定義され、特定のユーザーが所有しているドメインに依存している列を返します。<br /><br /> (COLUMN_DOMAIN_USAGE 行セット)|DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME COLUMN_NAME|  
|**adSchemaConstraintColumnUsage**|6|参照制約、unique 制約、check 制約、およびアサーションによって使用される列を返します。これらは、カタログで定義され、特定のユーザーによって所有されます。<br /><br /> (CONSTRAINT_COLUMN_USAGE 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME|  
|**adSchemaConstraintTableUsage**|7|参照制約、unique 制約、check 制約、および特定のユーザーが所有する、カタログで定義されているアサーションによって使用されるテーブルを返します。<br /><br /> (CONSTRAINT_TABLE_USAGE 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaCubes**|32|スキーマ (プロバイダーがスキーマをサポートしていない場合は、カタログ) で使用可能なキューブに関する情報を返します。<br /><br /> (キューブ行セット *)|CATALOG_NAME SCHEMA_NAME CUBE_NAME|  
|**Adschemadbin@ Keywords**|30|プロバイダー固有のキーワードの一覧を返します。<br /><br /> (IDBInfo:: GetKeywords)|\<> なし|  
|**Adschemadbin、**|31|テキストコマンドで使用されるプロバイダー固有のリテラルの一覧を返します。<br /><br /> (IDBInfo:: GetLiteralInfo)|\<> なし|  
|**adSchemaDimensions**|33|指定されたキューブ内のディメンションに関する情報を返します。 ディメンションごとに1つの行があります。<br /><br /> (ディメンション行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**adSchemaForeignKeys**|27|指定されたユーザーによってカタログで定義された外部キー列を返します。<br /><br /> (FOREIGN_KEYS 行セット)|PK_TABLE_CATALOG、PK_TABLE_SCHEMA、PK_TABLE_NAME、FK_TABLE_CATALOG、FK_TABLE_SCHEMA、FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|ディメンションで使用可能な階層に関する情報を返します。<br /><br /> (階層行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME|  
|**Adschemdemux**|12|特定のユーザーによって所有されているカタログに定義されているインデックスを返します。<br /><br /> (インデックス行セット)|TABLE_CATALOG TABLE_SCHEMA INDEX_NAME の種類 TABLE_NAME|  
|**adSchemaKeyColumnUsage**|8|指定されたユーザーによってキーとして制約されている、カタログで定義されている列を返します。<br /><br /> (KEY_COLUMN_USAGE 行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaLevels**|35|ディメンションで使用可能なレベルに関する情報を返します。<br /><br /> (レベル行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME|  
|**adschemameasame**|36|使用可能なメジャーに関する情報を返します。<br /><br /> (メジャー行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|使用可能なメンバーに関する情報を返します。<br /><br /> (MEMBERS 行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE ツリー演算子。 詳細については、「オンライン分析処理 (OLAP) の OLE DB」を参照してください。|  
|**adSchemaPrimaryKeys**|28|指定されたユーザーによってカタログで定義された主キー列を返します。<br /><br /> (PRIMARY_KEYS 行セット)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adSchemaProcedureColumns**|29|プロシージャによって返される行セットの列に関する情報を返します。<br /><br /> (PROCEDURE_COLUMNS 行セット)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**adSchemaProcedureParameters**|26|プロシージャのパラメーターとリターン コードに関する情報を返します。<br /><br /> (PROCEDURE_PARAMETERS 行セット)|PROCEDURE_CATALOG、PROCEDURE_SCHEMA、PROCEDURE_NAME、PARAMETER_NAME|  
|**adSchemaProcedures**|16|指定されたユーザーが所有する、カタログで定義されているプロシージャを返します。<br /><br /> (プロシージャ行セット)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE|  
|**adSchemaProperties**|37|ディメンションの各レベルで使用可能なプロパティに関する情報を返します。<br /><br /> (プロパティ行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**adSchemaProviderSpecific**|-1|プロバイダーが独自の非標準スキーマクエリを定義する場合に使用します。|\<プロバイダー固有の>|  
|**adSchemaProviderTypes**|22|データプロバイダーでサポートされている (基本) データ型を返します。<br /><br /> (PROVIDER_TYPES 行セット)|DATA_TYPE、BEST_MATCH|  
|**Adschemaて Entialconstraints**|9|特定のユーザーが所有する、カタログで定義されている参照制約を返します。<br /><br /> (REFERENTIAL_CONSTRAINTS 行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaSchemata**|17|特定のユーザーによって所有されているスキーマ (データベースオブジェクト) を返します。<br /><br /> (スキーマ行セット)|CATALOG_NAME、SCHEMA_NAME、SCHEMA_OWNER|  
|**adSchemaSQLLanguages**|18|カタログで定義されている SQL 実装処理データでサポートされている準拠レベル、オプション、および言語を返します。<br /><br /> (SQL_LANGUAGES 行セット)|\<> なし|  
|**adSchemaStatistics**|19|特定のユーザーによって所有されているカタログに定義されている統計を返します。<br /><br /> (統計行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaTableConstraints**|10|特定のユーザーが所有する、カタログで定義されているテーブル制約を返します。<br /><br /> (TABLE_CONSTRAINTS 行セット)|CONSTRAINT_CATALOG、CONSTRAINT_SCHEMA、CONSTRAINT_NAME、TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、CONSTRAINT_TYPE|  
|**adSchemaTablePrivileges**|14|特定のユーザーが使用できる、または特定のユーザーによって許可される、カタログで定義されているテーブルに対する権限を返します。<br /><br /> (TABLE_PRIVILEGES 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、GRANTOR、GRANTEE|  
|**adSchemaTables**|20|指定したユーザーがアクセスできる、カタログに定義されているテーブル (ビューを含む) を返します。<br /><br /> (テーブル行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、TABLE_TYPE|  
|**adschematranslran**|21|指定したユーザーがアクセスできる、カタログで定義されている文字変換を返します。<br /><br /> (翻訳行セット)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adSchemaTrustees**|39|将来使用するために予約されています。||  
|**Adschemaの特権**|15|特定のユーザーが使用できる、または特定のユーザーによって付与される、カタログで定義されているオブジェクトに対する使用権限を返します。<br /><br /> (USAGE_PRIVILEGES 行セット)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE 権限付与対象ユーザー|  
|**adSchemaViewColumnUsage**|24|カタログで定義され、特定のユーザーによって所有されている、表示されているテーブルが依存している列を返します。<br /><br /> (VIEW_COLUMN_USAGE 行セット)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adSchemaViews**|23|特定のユーザーがアクセスできる、カタログで定義されているビューを返します。<br /><br /> (ビュー行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaViewTableUsage**|25|カタログで定義され、特定のユーザーによって所有されている、表示されているテーブルが依存しているテーブルを返します。<br /><br /> (VIEW_TABLE_USAGE 行セット)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums セット|  
|AdoEnums 制約|  
|AdoEnums|  
|AdoEnums 特権|  
|AdoEnums|  
|AdoEnums DOMAINUSAGE|  
|AdoEnums. CONSTRAINTCOLUMNUSAGE|  
|AdoEnums. CONSTRAINTTABLEUSAGE|  
|AdoEnums|  
|AdoEnums. DBINFOKEYWORDS|  
|AdoEnums. DBINFOLITERALS|  
|AdoEnums|  
|AdoEnums. FOREIGNKEYS|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums の使用法|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums キー|  
|AdoEnums. PROCEDURECOLUMNS|  
|AdoEnums. PROCEDUREPARAMETERS|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums 固有のスキーマ|  
|AdoEnums 型|  
|AdoEnums. REFERENTIALCONTRAINTS|  
|AdoEnums. スキーマ|  
|AdoEnums. SQLLANGUAGES|  
|AdoEnums|  
|AdoEnums. TABLECONSTRAINTS|  
|AdoEnums 特権|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums 特権|  
|AdoEnums の使用方法|  
|AdoEnums|  
|AdoEnums の使用|  
  
## <a name="applies-to"></a>適用対象  
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)
