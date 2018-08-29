---
title: OLE DB API による機能強化された日付と時刻のサポート | Microsoft Docs
description: OLE DB API による機能強化された日付と時刻のサポート
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d23ec6fe80891bbbe09860e43d38db48789ce917
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024297"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB API による機能強化された日付と時刻のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|機能|[説明]|  
|--------------|-----------------|  
|Iaccessor::createaccessor|DBBINDING 構造体を識別するアプリケーションを有効にするフラグが追加**datetime**、 **datetime2**、および**smalldatetime**値。 詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IBCPSession::BCPColFmt|詳細については、次を参照してください。[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)します。|  
|ICommandWithParameters::GetParameterInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|ICommandWithParameters::SetParameterinfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IColumnsRowset::GetColumnsRowset|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|IColumnsInfo::GetColumnInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)します。|  
|Idbschemarowset::getrowset|影響を受けるスキーマ行セットの詳細については、次を参照してください。[日付と時刻、およびスキーマ行セット](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)します。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|Itabledefinition::createtable|詳細については、次を参照してください。 [OLE DB の日付と時刻の強化に対するデータ型のサポート](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)します。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化機能 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
