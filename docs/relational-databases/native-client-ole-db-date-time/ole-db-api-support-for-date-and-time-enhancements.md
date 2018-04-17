---
title: 日付と時刻の機能強化の OLE DB API によるサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2bb9297fb502e27e39750b19a239ed2de427397e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>日付と時刻の機能強化の OLE DB API によるサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|関数|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|区別するアプリケーションを有効にする DBBINDING 構造体にフラグが追加**datetime**、 **datetime2**、および**smalldatetime**値。 詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IBCPSession::BCPColFmt|詳細については、次を参照してください。[強化された日付と時刻型の変更の一括コピー &#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)です。|  
|ICommandWithParameters::GetParameterInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|ICommandWithParameters::SetParameterinfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IColumnsRowset::GetColumnsRowset|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IColumnsInfo::GetColumnInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、「[日付と時刻、およびスキーマ行セット](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)です。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、次を参照してください。 [OLE DB の日付と時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)です。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化 (&) #40";"OLE DB"&"#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
