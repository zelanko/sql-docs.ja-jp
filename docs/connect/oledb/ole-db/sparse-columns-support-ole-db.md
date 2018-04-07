---
title: スパース列のサポート (OLE DB) |Microsoft ドキュメント
description: スパース列のサポート (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 327c98688395be4afd5381387be6b6675eae3981
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="sparse-columns-support-ole-db"></a>スパース列のサポート (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、スパース列の SQL Server のサポートの OLE DB ドライバーに関する情報を提供します。 スパース列の詳細については、次を参照してください。 [OLE DB Driver for SQL Server でスパース列のサポート](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)です。 サンプルについては、次を参照してください。[表示列およびカタログ メタデータのスパース列の&#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)です。  
  
## <a name="ole-db-statement-metadata"></a>OLE DB ステートメント メタデータ  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、新しい DBCOLUMNFLAGS フラグ値である DBCOLUMNFLAGS_SS_ISCOLUMNSET を使用できます。 ある列に対するこの値を設定する必要があります**column_set**値。 DBCOLUMNFLAGS フラグを使用して取得できます、 *dwFlags* icolumnsinfo::getcolumnsinfo と icolumnsrowset::getcolumnsrowset によって返される行セットの DBCOLUMN_FLAGS 列のパラメーターです。  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB カタログ メタデータ  
 DBSCHEMA_COLUMNS に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の列が 2 つ追加されています。  
  
|列名|データ型|値およびコメント|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|列がスパース列の場合は VARIANT_TRUE、それ以外の場合は VARIANT_FALSE になります。|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|列がスパースの場合**column_set**列で、これは、値 VARIANT_TRUE、それ以外の VARIANT_FALSE です。|  
  
 また、2 つのスキーマ行セットが追加されています。 これらの行セットは、構造は DBSCHEMA_COLUMNS と同じですが、返される内容が異なります。 DBSCHEMA_COLUMNS_EXTENDED は、すべての列に関係なくを返します**column_set**メンバーシップです。 DBSCHEMA_SPARSE_COLUMN_SET は、スパースのメンバーである列のみを返します**column_set**です。  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility の動作  
 動作**DataTypeCompatibility = 80** (、接続文字列に) と整合性が、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]次のように、クライアント。  
  
-   新しいスキーマ行セットは表示されず、スキーマ行セットの行セットにそれらのスキーマ行セットの行は含まれません。  
  
-   COLUMNS 行セット内の新しい列は表示されません。  
  
-   ある DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されていない**column_set**列です。  
  
-   DBCOMPUTEMODE_NOTCOMPUTED に設定されている**column_set**列です。  
  
## <a name="ole-db-support-for-sparse-columns"></a>OLE DB によるスパース列のサポート  
 OLE DB Driver for SQL Server のスパース列をサポートするために、次の OLE DB インターフェイスが変更されました。  
  
|型またはメンバー関数|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|新しい DBCOLUMNFLAGS フラグ値のある DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されている**column_set**内の列*dwFlags*です。<br /><br /> DBCOLUMNFLAGS_WRITE に設定されている**column_set**列です。|  
|IColumsRowset::GetColumnsRowset|設定は、新しい DBCOLUMNFLAGS フラグ値である DBCOLUMNFLAGS_SS_ISCOLUMNSET が**column_set** DBCOLUMN_FLAGS 内の列です。<br /><br /> DBCOLUMN_COMPUTEMODE が DBCOMPUTEMODE_DYNAMIC 用に設定されている**column_set**列です。|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS が、SS_IS_COLUMN_SET と SS_IS_SPARSE という 2 つの新しい列を返します。<br /><br /> DBSCHEMA_COLUMNS がのメンバーではない列のみを返します、 **column_set**です。<br /><br /> 2 つの新しいスキーマ行セットが追加されました。 DBSCHEMA_COLUMNS_EXTENDED はのスパースかどうかに関係なくすべての列を返します**column_set**メンバーシップです。 DBSCHEMA_SPARSE_COLUMN_SET のメンバーである列のみが返されます、 **column_set**です。 これらの新しい行セットの列と制限は DBSCHEMA_COLUMNS と同じです。|  
|IDBSchemaRowset::GetSchemas|Idbschemarowset::getschemas には、使用可能なスキーマ行セットの一覧である DBSCHEMA_COLUMNS_EXTENDED と DBSCHEMA_SPARSE_COLUMN_SET の新しい行セットの Guid が含まれています。|  
|ICommand::Execute|場合**選択\*から***テーブル*は、スパースのメンバーではないすべての列が返されます使用、 **column_set**、すべての値を含む XML 列null 以外の列、スパースのメンバーである**column_set**存在する場合、します。|  
|IOpenRowset::OpenRowset|Iopenrowset::openrowset で icommand::execute と同じ列を含む行セットが返されます、**選択\***同じテーブルにクエリします。|  
|ITableDefinition|スパース列も、このインターフェイスへの変更がない**column_set**列です。 スキーマを変更する必要のあるアプリケーションでは、適切な [!INCLUDE[tsql](../../../includes/tsql-md.md)] を直接実行する必要があります。|  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
