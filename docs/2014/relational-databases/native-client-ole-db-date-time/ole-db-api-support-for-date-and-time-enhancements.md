---
title: 日付と時刻の機能強化の OLE DB API によるサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bf7eee4dd2517d4ff9c9f871160ba0515b18ce8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178646"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>日付と時刻の機能強化の OLE DB API によるサポート
  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|機能|説明|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|アプリケーションで `datetime`、`datetime2`、および `smalldatetime` の各値を区別できるように、DBBINDING 構造体にフラグが用意されています。 詳細については、次を参照してください。[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)です。|  
|IBCPSession::BCPColFmt|詳細については、次を参照してください。[強化された日付と時刻型の変更の一括コピー &#40;OLE DB および ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)です。|  
|ICommandWithParameters::GetParameterInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)です。|  
|ICommandWithParameters::SetParameterinfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)です。|  
|IColumnsRowset::GetColumnsRowset|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)です。|  
|IColumnsInfo::GetColumnInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)です。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、「[日付と時刻、およびスキーマ行セット](../native-client-ole-db-rowsets/rowsets.md)です。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、次を参照してください。 [OLE DB の日付と時刻の強化に対するデータ型のサポート](data-type-support-for-ole-db-date-and-time-improvements.md)です。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化&#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  