---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69ba76725f5a5d3b21224495554cc2a419265f7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299922"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  エラーの詳細を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]含むネイティブ クライアント OLE DB プロバイダー SSERRORINFO 構造体へのポインターを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、 **ISQLServerErrorInfo** エラー インターフェイスを定義します。 このインターフェイスは、重大度や状態など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの詳細情報を返します。  

  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>引数  
 *ppSSErrorInfo*[out]  
 SSERRORINFO 構造体へのポインター。 メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppSSErrorInfo* 引数に NULL ポインターを設定します。  
  
 *ppErrorStrings*[out]  
 Unicode 文字列ポインターへのポインター。 メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppErrorStrings* 引数に NULL ポインターを設定します。 **IMalloc::Free** メソッドを使用して *ppErrorStrings* 引数を解放すると、メモリがブロック単位で割り当てられているので、結果の SSERRORINFO 構造体の 3 つの各文字列メンバーが解放されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_INVALIDARG  
 *ppSSErrorInfo* または *ppErrorStrings* 引数のいずれかが NULL でした。  
  
 E_OUTOFMEMORY  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダは、要求を完了するために十分なメモリを割り当てることができませんでした。  
  
## <a name="remarks"></a>解説  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、コンシューマーによって渡されるポインターを通じて返される SSERRORINFO および OLECHAR 文字列のメモリを割り当てます。 コンシューマーはエラー データにアクセスする必要がなくなった時点で、**IMalloc::Free** メソッドを使用してこのメモリの割り当てを解除する必要があります。  
  
 SSERRORINFO 構造体は、次のように定義されています。  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|メンバー|説明|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージ。 このメッセージは、**IErrorInfo::GetDescription** メソッドにより返されます。|  
|*pwszServer*|エラーが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|*pwszProcedure*|エラーがストアド プロシージャ内で発生している場合は、エラーが発生したストアド プロシージャの名前です。それ以外の場合は、空文字列になります。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号。 このエラー番号は、**ISQLErrorInfo::GetSQLInfo** メソッドの *plNativeError* パラメーターに返されるものと同じになります。|  
|*bState*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの状態。|  
|*bClass*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの重大度。|  
|*wLineNumber*|該当する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャのエラー メッセージを生成した行です。 プロシージャが関係していない場合は、既定値 1 が使用されます。|  
  
 構造体内のポインターは、*ppErrorStrings* 引数に返される文字列内のアドレスを指します。  
  
## <a name="see-also"></a>参照  
 [OLE DB&#41;&#40;エラー情報](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
