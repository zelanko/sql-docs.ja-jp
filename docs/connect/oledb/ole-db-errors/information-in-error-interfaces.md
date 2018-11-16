---
title: エラー インターフェイス内の情報 |Microsoft Docs
description: エラー インターフェイス内の情報
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: c80013249af94a2ad94c221bc6155dca7c7d2664
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606762"
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server は、OLE DB 定義のエラー インターフェイス **IErrorInfo**、**IErrorRecords**、および **ISQLErrorInfo** によって、一部のエラーと状態情報を報告します。  
  
 OLE DB Driver for SQL Server サポート**IErrorInfo**メンバー関数を次のようにします。  
  
|メンバー関数|[説明]|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常に 0 を返します。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列 "Microsoft OLE DB Driver for SQL Server"。|  
  
 コンシューマーが使用できる、OLE DB Driver for SQL Server をサポート**IErrorRecords**メンバー関数を次のようにします。  
  
|メンバー関数|[説明]|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|**ISQLErrorInfo** インターフェイスと [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) インターフェイスの参照を返します。|  
|**GetErrorInfo**|**IErrorInfo** インターフェイスの参照を返します。|  
|**GetErrorParameters**|経由でコンシューマーにパラメーターが、OLE DB Driver for SQL Server に戻らない**GetErrorParameters**します。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 OLE DB Driver for SQL Server サポート**isqlerrorinfo::getsqlinfo**パラメーターとして次のとおりです。  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 どちらも[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]OLE DB Driver for SQL Server には、実装に固有の SQLSTATE 値が定義されているとします。|  
|*plNativeError*|該当する場合は、**master.dbo.sysmessages** から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエラー番号を返します。 ネイティブ エラーは、成功した試行を OLE DB Driver for SQL Server データ ソースを初期化するために使用できます。 試行する前に、OLE DB Driver for SQL Server は常に 0 を返します。|  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
