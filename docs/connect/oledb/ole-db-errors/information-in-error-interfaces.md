---
title: エラー インターフェイス内の情報 |Microsoft ドキュメント
description: エラー インターフェイス内の情報
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4f79c469f40c778342e1093df0386acee80890de
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server が OLE DB 定義のエラー インターフェイスの一部のエラーと状態情報を報告**IErrorInfo**、 **IErrorRecords**、および**ISQLErrorInfo**です。  
  
 SQL Server の OLE DB ドライバーをサポートしている**IErrorInfo**メンバーが次のように機能します。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常に 0 を返します。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列"Microsoft OLE DB Driver for SQL Server"です。|  
  
 SQL Server の OLE DB ドライバーをサポートしているコンシューマーが使用できる**IErrorRecords**メンバーが次のように機能します。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|インターフェイスの参照を返します**ISQLErrorInfo、**と[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)です。|  
|**GetErrorInfo**|参照を返します、 **IErrorInfo**インターフェイスです。|  
|**GetErrorParameters**|SQL Server の OLE DB Driver は、経由でコンシューマーにパラメーターを返しません**GetErrorParameters**です。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 SQL Server の OLE DB ドライバーをサポートしている**isqlerrorinfo::getsqlinfo**パラメーターは次のようにします。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 どちらも[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]OLE DB Driver for SQL Server には、実装に固有の SQLSTATE 値が定義されているとします。|  
|*plNativeError*|返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のエラー番号**master.dbo.sysmessages**使用可能な場合です。 ネイティブのエラーは、OLE DB Driver for SQL Server データ ソースの初期化が成功するの後に使用できます。 試行する前に、OLE DB Driver for SQL Server は常に 0 を返します。|  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
