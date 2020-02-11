---
title: エラーインターフェイス内の情報 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60b6b0387aea5475d74c314a10e4fa437fadc005
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62657662"
---
# <a name="information-in-error-interfaces"></a>エラー インターフェイス内の情報
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、OLE DB 定義されたエラーインターフェイス**IErrorInfo**、 **ierrorrecords**、 **ISQLErrorInfo**でエラーと状態に関する情報を報告します。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、次のように**IErrorInfo**メンバー関数をサポートしています。  
  
|メンバー関数|[説明]|  
|---------------------|-----------------|  
|**GetDescription**|エラー メッセージを説明する文字列を返します。|  
|**GetGUID**|エラーを定義したインターフェイスの GUID を返します。|  
|**GetHelpContext**|サポートされていません。 常にゼロが返されます。|  
|**GetHelpFile**|サポートされていません。 常に NULL が返されます。|  
|**GetSource**|文字列 "Microsoft SQL Server Native Client" を返します。|  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、次のように、コンシューマーが使用できる**ierrorrecords**メンバー関数をサポートしています。  
  
|メンバー関数|[説明]|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|エラーに関する基本情報を ERRORINFO 構造体に設定します。 ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。|  
|**GetCustomErrorObject**|
  **ISQLErrorInfo** インターフェイスと [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) インターフェイスの参照を返します。|  
|**GetErrorInfo**|
  **IErrorInfo** インターフェイスの参照を返します。|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、 **GetErrorParameters**を介してコンシューマーにパラメーターを返しません。|  
|**GetRecordCount**|使用できるエラー レコードの数を返します。|  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーでは、次のように**ISQLErrorInfo:: GetSQLInfo**パラメーターがサポートされています。  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|*pbstrSQLState*|エラーの SQLSTATE 値を返します。 SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB プロバイダーのどちらも、実装固有の SQLSTATE 値を定義していません。|  
|*Pl・エラー*|該当する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]master.dbo.sysmessages** から ** のエラー番号を返します。 ネイティブクライアント OLE DB プロバイダーのデータソースを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]正常に初期化しようとすると、ネイティブエラーが発生します。 この試行の前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に0を返します。|  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
