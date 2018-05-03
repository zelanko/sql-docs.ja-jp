---
title: SchemaEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SchemaEnum
helpviewer_keywords:
- SchemaEnum enumeration [ADO]
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d2904852d7e44e28eb4ad1331f1276f3ef45234
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="schemaenum"></a>SchemaEnum
スキーマの種類を指定**Recordset**を[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドを取得します。  
  
## <a name="remarks"></a>解説  
 各 ADO 定数は含まれてのトピックでの関数と列に関する追加情報が返された[付録 B スキーマ行セット](http://msdn.microsoft.com/en-us/2b5fbf03-e50d-44ee-bc57-5a57666c55f1)の OLE DB プログラマーズ リファレンスです。 各トピックの名前は、次の表の説明 セクションでは、かっこに表示されます。  
  
 各 ADO MD 定数は含まれてのトピックでの関数と列に関する追加情報が返された[OLE DB for OLAP オブジェクトおよびスキーマ行セット](http://msdn.microsoft.com/en-us/d20bb2a6-68bd-423f-9ec8-eb930cd0c144)OLE DB for Online Analytical Processing (OLAP) のドキュメントにします。 各トピックの名前は、次の表の説明の列内のかっこに表示されます。  
  
 ADO データ型に、OLE DB のドキュメント内の列のデータ型を変換すると、必要な ADO の説明の列を参照して[格納](../../../ado/reference/ado-api/datatypeenum.md)トピックです。 など、OLE DB データ型の**DBTYPE_WSTR**の ADO データ型に相当**adWChar**です。  
  
 ADO には、定数、スキーマのような結果が生成されます。 **adSchemaDBInfoKeywords**と**adSchemaDBInfoLiterals**です。 ADO を作成、 **Recordset**、し、それぞれによって返される値を使用して各行を格納、 **IDBInfo::GetKeywords**と**IDBInfo::GetLiteralInfo**メソッドです。 これらのメソッドに関する追加情報は含まれて、 [IDBInfo](http://msdn.microsoft.com/en-us/3f5ad97f-3fc6-4f21-b691-f6911e4007f3)の OLE DB プログラマーズ リファレンスのセクションです。  
  
|定数|値|Description|制約列|  
|--------------|-----------|-----------------|------------------------|  
|**adSchemaAsserts**|0|特定のユーザーによって所有されているカタログで定義されているアサーションを返します。<br /><br /> (アサーションの行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCatalogs**|1|DBMS からアクセス可能なカタログに関連付けられている物理属性を返します。<br /><br /> (行セットのカタログ)|CATALOG_NAME|  
|**adSchemaCharacterSets**|2|カタログで定義されている、指定されたユーザーがアクセスできる文字セットを返します。<br /><br /> (CHARACTER_SETS 行セット)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adSchemaCheckConstraints**|5|特定のユーザーによって所有されているカタログで定義された check 制約を返します。<br /><br /> (CHECK_CONSTRAINTS)行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCollations**|3|文字の照合順序、カタログで定義されている特定のユーザーにアクセスできるを返します。<br /><br /> (行セットの照合順序)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adSchemaColumnPrivileges**|13|カタログで定義されているユーザーが利用できる、または特定のユーザーによって付与されるテーブル列の権限を返します。<br /><br /> (Column_privileges も行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME、GRANTOR、GRANTEE|  
|**adSchemaColumns**|4|テーブル (ビューを含む)、カタログで定義されている特定のユーザーにアクセス可能である列を返します。<br /><br /> (COLUMNS 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME|  
|**adSchemaColumnsDomainUsage**|11|カタログで定義されているし、特定のユーザーが所有するドメインに依存しているカタログで定義されている列を返します。<br /><br /> (COLUMN_DOMAIN_USAGE 行セット)|DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME COLUMN_NAME|  
|**adSchemaConstraintColumnUsage**|6|参照制約、unique 制約、check 制約、およびアサーションによって使用される、カタログで定義されているし、特定のユーザーが所有する列を返します。<br /><br /> (CONSTRAINT_COLUMN_USAGE 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME|  
|**adSchemaConstraintTableUsage**|7|参照制約、unique 制約、check 制約、およびカタログで定義され、特定のユーザーによって所有アサーションによって使用されているテーブルを返します。<br /><br /> (CONSTRAINT_TABLE_USAGE 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaCubes**|32|スキーマ (または、カタログは、プロバイダーがスキーマをサポートしていない場合) で利用可能なキューブに関する情報を返します。<br /><br /> (キューブ行セット *)|CATALOG_NAME SCHEMA_NAME CUBE_NAME|  
|**adSchemaDBInfoKeywords**|30|プロバイダー固有のキーワードの一覧を返します。<br /><br /> (IDBInfo::GetKeywords)|\<なし >|  
|**adSchemaDBInfoLiterals**|31|テキスト コマンドで使用されるプロバイダー固有のリテラルの一覧を返します。<br /><br /> (IDBInfo::GetLiteralInfo)|\<なし >|  
|**adSchemaDimensions**|33|特定のキューブ ディメンションに関する情報を返します。 各ディメンションの 1 つの行があります。<br /><br /> (ディメンション行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**adSchemaForeignKeys**|27|特定のユーザーによってカタログで定義されている外部キー列を返します。<br /><br /> (FOREIGN_KEYS 行セット)|PK_TABLE_CATALOG、PK_TABLE_SCHEMA、PK_TABLE_NAME、FK_TABLE_CATALOG、FK_TABLE_SCHEMA、FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|ディメンションの使用可能な階層についての情報を返します。<br /><br /> (階層行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME|  
|**adSchemaIndexes**|12|特定のユーザーによって所有されているカタログで定義されているインデックスを返します。<br /><br /> (インデックス行セット)|TABLE_CATALOG、TABLE_SCHEMA、INDEX_NAME 型 TABLE_NAME|  
|**adSchemaKeyColumnUsage**|8|キーとして特定のユーザーによって制限されているカタログで定義されている列を返します。<br /><br /> (KEY_COLUMN_USAGE 行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME|  
|**adSchemaLevels**|35|ディメンションで利用できるレベルに関する情報を返します。<br /><br /> (行セットのレベル)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME される LEVEL_UNIQUE_NAME|  
|**adSchemaMeasures**|36|使用できるメジャーに関する情報を返します。<br /><br /> (MEASURES 行セット)|CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|利用可能なメンバーに関する情報を返します。<br /><br /> (行セットのメンバー)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME される LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE ツリー演算子です。 詳細については、のオンライン分析処理 (OLAP) の OLE DB を参照してください。|  
|**adSchemaPrimaryKeys**|28|特定のユーザーによってカタログで定義されている主キー列を返します。<br /><br /> (PRIMARY_KEYS 行セット)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adSchemaProcedureColumns**|29|プロシージャによって返される行セットの列に関する情報を返します。<br /><br /> (PROCEDURE_COLUMNS 行セット)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**adSchemaProcedureParameters**|26|プロシージャのパラメーターとリターン コードに関する情報を返します。<br /><br /> (PROCEDURE_PARAMETERS 行セット)|PROCEDURE_CATALOG、PROCEDURE_SCHEMA、PROCEDURE_NAME、PARAMETER_NAME|  
|**adSchemaProcedures**|16|特定のユーザーによって所有されているカタログで定義されているプロシージャを返します。<br /><br /> (プロシージャ行セット)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE|  
|**adSchemaProperties**|37|ディメンションのレベルごとに使用可能なプロパティに関する情報を返します。<br /><br /> (行セットのプロパティ)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME される LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**adSchemaProviderSpecific**|-1|プロバイダーには、独自の標準スキーマ クエリが定義されている場合に使用します。|\<プロバイダー固有 >|  
|**adSchemaProviderTypes**|22|データ プロバイダーでサポートされている (基本) データ型を返します。<br /><br /> (PROVIDER_TYPES 行セット)|DATA_TYPE、BEST_MATCH|  
|**AdSchemaReferentialConstraints**|9|特定のユーザーによって所有されているカタログで定義されている参照に関する制約を返します。<br /><br /> (REFERENTIAL_CONSTRAINTS 行セット)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaSchemata**|17|特定のユーザーによって所有されているスキーマ (データベース オブジェクト) を返します。<br /><br /> (スキーマ行セット)|CATALOG_NAME、SCHEMA_NAME、SCHEMA_OWNER|  
|**adSchemaSQLLanguages**|18|準拠レベル、オプション、およびカタログで定義されているデータには、SQL 実装処理によってサポートされている言語を返します。<br /><br /> (SQL_LANGUAGES 行セット)|\<なし >|  
|**adSchemaStatistics**|19|特定のユーザーによって所有されているカタログで定義されている統計を返します。<br /><br /> (統計の行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaTableConstraints**|10|特定のユーザーによって所有されているカタログで定義されているテーブル制約を返します。<br /><br /> (TABLE_CONSTRAINTS 行セット)|CONSTRAINT_CATALOG、CONSTRAINT_SCHEMA、CONSTRAINT_NAME、TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、CONSTRAINT_TYPE|  
|**adSchemaTablePrivileges**|14|カタログで定義されているユーザーが利用できる、または特定のユーザーによって付与されるテーブルの特権を返します。<br /><br /> (TABLE_PRIVILEGES 行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、GRANTOR、GRANTEE|  
|**adSchemaTables**|20|テーブル (ビューを含む)、カタログで定義されている特定のユーザーにアクセスできるを返します。<br /><br /> (テーブル行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、TABLE_TYPE|  
|**adSchemaTranslations**|21|カタログで定義されている、指定されたユーザーがアクセスできる文字変換を返します。<br /><br /> (翻訳行セット)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adSchemaTrustees**|39|将来の使用のために予約されています。||  
|**adSchemaUsagePrivileges**|15|カタログで定義されているユーザーが利用できる、または特定のユーザーによって付与されるオブジェクトの使用権限を返します。<br /><br /> (USAGE_PRIVILEGES 行セット)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE、GRANTOR、GRANTEE|  
|**adSchemaViewColumnUsage**|24|返し、列がテーブルの表示、カタログで定義されている特定のユーザーによって所有されているは、依存します。<br /><br /> (VIEW_COLUMN_USAGE 行セット)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adSchemaViews**|23|特定のユーザーにアクセス可能である、カタログで定義されているビューを返します。<br /><br /> (ビューの行セット)|TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME|  
|**adSchemaViewTableUsage**|25|依存するが、テーブルを表示、カタログで定義および特定のユーザーによって所有するテーブルを返します。<br /><br /> (VIEW_TABLE_USAGE 行セット)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Schema.ASSERTS|  
|AdoEnums.Schema.CATALOGS|  
|AdoEnums.Schema.CHARACTERSETS|  
|AdoEnums.Schema.CHECKCONSTRAINTS|  
|AdoEnums.Schema.COLLATIONS|  
|AdoEnums.Schema.COLUMNPRIVILEGES|  
|AdoEnums.Schema.COLUMNS|  
|AdoEnums.Schema.COLUMNSDOMAINUSAGE|  
|AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE|  
|AdoEnums.Schema.CONSTRAINTTABLEUSAGE|  
|AdoEnums.Schema.CUBES|  
|AdoEnums.Schema.DBINFOKEYWORDS|  
|AdoEnums.Schema.DBINFOLITERALS|  
|AdoEnums.Schema.DIMENSIONS|  
|AdoEnums.Schema.FOREIGNKEYS|  
|AdoEnums.Schema.HIERARCHIES|  
|AdoEnums.Schema.INDEXES|  
|AdoEnums.Schema.KEYCOLUMNUSAGE|  
|AdoEnums.Schema.LEVELS|  
|AdoEnums.Schema.MEASURES|  
|AdoEnums.Schema.MEMBERS|  
|AdoEnums.Schema.PRIMARYKEYS|  
|AdoEnums.Schema.PROCEDURECOLUMNS|  
|AdoEnums.Schema.PROCEDUREPARAMETERS|  
|AdoEnums.Schema.PROCEDURES|  
|AdoEnums.Schema.PROPERTIES|  
|AdoEnums.Schema.PROVIDERSPECIFIC|  
|AdoEnums.Schema.PROVIDERTYPES|  
|AdoEnums.Schema.REFERENTIALCONTRAINTS|  
|AdoEnums.Schema.SCHEMATA|  
|AdoEnums.Schema.SQLLANGUAGES|  
|AdoEnums.Schema.STATISTICS|  
|AdoEnums.Schema.TABLECONSTRAINTS|  
|AdoEnums.Schema.TABLEPRIVILEGES|  
|AdoEnums.Schema.TABLES|  
|AdoEnums.Schema.TRANSLATIONS|  
|AdoEnums.Schema.TRUSTEES|  
|AdoEnums.Schema.USAGEPRIVILEGES|  
|AdoEnums.Schema.VIEWCOLUMNUSAGE|  
|AdoEnums.Schema.VIEWS|  
|AdoEnums.Schema.VIEWTABLEUSAGE|  
  
## <a name="applies-to"></a>適用対象  
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)
