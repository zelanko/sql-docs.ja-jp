---
title: OLE DB API による機能強化された日付と時刻のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94bb860df5a9ee2f3b125f6e05c6ff5adb44db99
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773426"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB API による機能強化された日付と時刻のサポート
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|アプリケーションで **datetime**、**datetime2**、**smalldatetime** 値を区別できるように、DBBINDING 構造体にフラグが追加されます。 詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IBCPSession::BCPColFmt|詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。|  
|ICommandWithParameters::GetParameterInfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|ICommandWithParameters::SetParameterinfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsRowset::GetColumnsRowset|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsInfo::GetColumnInfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットについては、「[日付、時刻、スキーマ行セット](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)」を参照してください。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、「[OLE DB の日付/時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)」を参照してください。|  
  
## <a name="see-also"></a>関連項目  
 [日付と時刻の強化機能 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
