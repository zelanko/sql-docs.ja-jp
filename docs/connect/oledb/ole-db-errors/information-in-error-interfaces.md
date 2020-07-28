---
title: エラー インターフェイス内の情報
description: OLE DB Driver for SQL Server では、OLE DB 定義のエラー インターフェイス IErrorInfo、IErrorRecords、ISQLErrorInfo によって、一部のエラーと状態情報が報告されます。
ms.custom: ''
ms.date: 05/06/2020
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
ms.openlocfilehash: f398cb4ca6cdeaa9484e01b5ca41ae28b7d9f095
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003360"
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server は、OLE DB 定義のエラー インターフェイス **IErrorInfo**、**IErrorRecords**、および **ISQLErrorInfo** によって、一部のエラーと状態情報を報告します。  
  
 OLE DB Driver for SQL Server では、次の **IErrorInfo** メンバー関数がサポートされています。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常にゼロが返されます。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列 "Microsoft OLE DB Driver for SQL Server"。|  
  
 OLE DB Driver for SQL Server では、コンシューマーが使用できる、次の **IErrorRecords** メンバー関数がサポートされています。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|**ISQLErrorInfo** インターフェイスと [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) インターフェイスの参照を返します。|  
|**GetErrorInfo**|**IErrorInfo** インターフェイスの参照を返します。|  
|**GetErrorParameters**|OLE DB Driver for SQL Server では、**GetErrorParameters** 経由でコンシューマーにパラメーターを返すことはありません。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 OLE DB Driver for SQL Server では、次の **ISQLErrorInfo::GetSQLInfo** パラメーターがサポートされています。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または OLE DB Driver for SQL Server でも、実装固有の SQLSTATE 値は定義されません。|  
|*plNativeError*|該当する場合は、**master.dbo.sysmessages** から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエラー番号を返します。 OLE DB Driver for SQL Server のデータ ソースの初期化の試行が成功すると、ネイティブ エラーが使用できるようになります。 この試行の前は、OLE DB Driver for SQL Server では常に 0 が返されます。|  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
