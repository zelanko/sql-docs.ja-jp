---
title: エラー インターフェイス内の情報 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f6718692e07fb6037d7ffcea7b21d94fdca3181
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056275"
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB 定義されたエラーインターフェイス**IErrorInfo**、 **Ierrorrecords**、 **ISQLErrorInfo**でエラーと状態に関する情報を報告します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、次のように**IErrorInfo**メンバー関数をサポートしています。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常にゼロが返されます。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列 "Microsoft SQL Server Native Client" を返します。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、次のように、コンシューマーが使用できる**Ierrorrecords**メンバー関数をサポートしています。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|**ISQLErrorInfo** インターフェイスと [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) インターフェイスの参照を返します。|  
|**GetErrorInfo**|**IErrorInfo** インターフェイスの参照を返します。|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **GetErrorParameters**を介してコンシューマーにパラメーターを返しません。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 Native Client OLE DB プロバイダーでは、次のように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ISQLErrorInfo:: GetSQLInfo**パラメーターがサポートされています。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのどちらも、実装固有の SQLSTATE 値を定義していません。|  
|*plNativeError*|該当する場合は、**master.dbo.sysmessages** から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号を返します。 ネイティブクライアント OLE DB プロバイダーのデータソースを正常に初期化しようとすると、ネイティブエラーが発生し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 この試行の前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に0を返します。|  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
