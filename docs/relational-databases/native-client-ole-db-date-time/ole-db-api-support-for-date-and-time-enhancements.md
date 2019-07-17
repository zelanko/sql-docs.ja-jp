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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f99055c13cf04f15d652f79258b10654410e98c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909244"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB API による機能強化された日付と時刻のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|DBBINDING 構造体を識別するアプリケーションを有効にするフラグが追加**datetime**、 **datetime2**、および**smalldatetime**値。 詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IBCPSession::BCPColFmt|詳細については、次を参照してください。[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)します。|  
|ICommandWithParameters::GetParameterInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|ICommandWithParameters::SetParameterinfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IColumnsRowset::GetColumnsRowset|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IColumnsInfo::GetColumnInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、次を参照してください。[日付と時刻、およびスキーマ行セット](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)します。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、次を参照してください。 [OLE DB の日付と時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)します。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化機能 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
