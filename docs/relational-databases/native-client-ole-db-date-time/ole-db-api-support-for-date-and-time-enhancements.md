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
ms.openlocfilehash: e1d995abd5bb718e9e1df1e2d5af5d1c22769014
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73772334"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB API による機能強化された日付と時刻のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|Function|[説明]|  
|--------------|-----------------|  
|IAccessor:: CreateAccessor|DBBINDING 構造体にフラグが追加され、アプリケーションが**datetime**、 **datetime2**、および**smalldatetime**の各値を区別できるようになります。 詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IBCPSession::BCPColFmt|詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。|  
|ICommandWithParameters::GetParameterInfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|ICommandWithParameters::SetParameterinfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsRowset::GetColumnsRowset|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsInfo::GetColumnInfo|詳細については、「[パラメーターと行セットのメタデータ](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md)」を参照してください。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、「[日付と時刻およびスキーマ行セット](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)」を参照してください。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、「 [OLE DB の日付と時刻の機能強化に関するデータ型のサポート](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [OLE DB &#40;の日付と時刻の改善&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
