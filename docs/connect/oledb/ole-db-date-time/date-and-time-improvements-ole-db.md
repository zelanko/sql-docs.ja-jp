---
title: 日付と時刻の強化 (OLE DB) |Microsoft Docs
description: 日付と時刻の強化機能 (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 15c59e5b6f99eeec00d73741db33ef3331196249
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810076"
---
# <a name="date-and-time-improvements-ole-db"></a>日付と時刻の強化機能 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] では、新しい日付と時刻のデータ型が導入されています。 このセクションでは、SQL Server のこれらの新しい種類が OLE DB ドライバーの拡張機能として公開する方法について説明します。 新しい日付と時刻のデータ型の SQL Server のサポートの OLE DB ドライバーの概要については、次を参照してください。[日付と時刻の強化](../../oledb/features/date-and-time-improvements.md)します。 サンプルについては、次を参照してください。[使用の強化された日付と時刻の機能&#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)します。  
  
 日付と時刻のデータ型についての一般的なは、次を参照してください。 [datetime &#40;TRANSACT-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [OLE DB の日付/時刻の強化に対するデータ型のサポート](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 OLE DB (OLE DB Driver for SQL Server) に関する情報の種類をサポートする提供[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]日付と時刻のデータ型。  
  
 [メタデータ&#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 DBBINDING 構造体に関する情報を格納**icommandwithparameters::getparameterinfo**、 **icommandwithparameters::setparameterinfo**、 **IColumnsRowset:。GetColumnsRowset**と**ColumnsInfo::GetColumnInfo**します。 また、OLE DB スキーマ行セットの更新についても説明します。  
  
 [バインドと変換 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 既存の日付型と新しい日付型の両方を対象とした、サーバーとクライアント間における変換の規則について説明します。  
  
 [機能強化された日付型と時刻型向けの一括コピーの変更 (OLE DB)](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 一括コピー操作をサポートする日付または時刻の機能強化について説明します。  
  
 [OLE DB API による機能強化された日付と時刻のサポート](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 機能強化された日付や時刻をサポートする OLE DB API について説明します。  
  
 [IRowsetFind での比較](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 日付/時刻型について説明しますと**IRowsetFind**します。  
 
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
