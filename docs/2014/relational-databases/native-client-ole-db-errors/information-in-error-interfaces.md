---
title: エラー インターフェイス内の情報 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a121dc2e94c67637e867398bfa40c7fe230cd411
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419021"
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、OLE DB 定義のエラー インターフェイス内のいくつかのエラーと状態情報を報告する**IErrorInfo**、 **IErrorRecords**、および**ISQLErrorInfo**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのサポート**IErrorInfo**メンバー関数を次のようにします。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常に 0 を返します。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列 "Microsoft SQL Server Native Client" を返します。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コンシューマーが使用できるサポート**IErrorRecords**メンバー関数を次のようにします。  
  
|メンバー関数|説明|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|インターフェイスの参照を返します**ISQLErrorInfo、** と[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)します。|  
|**GetErrorInfo**|参照を返します、 **IErrorInfo**インターフェイス。|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー経由でコンシューマーにパラメーターを返さない**GetErrorParameters**します。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのサポート**isqlerrorinfo::getsqlinfo**パラメーターとして次のとおりです。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 どちらも[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]も[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーが実装に固有の SQLSTATE 値を定義します。|  
|*plNativeError*|返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのエラー番号**master.dbo.sysmessages**使用可能な場合。 ネイティブ エラーは、初期化に成功したときに使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのデータ ソース。 試行する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に 0 を返します。|  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
