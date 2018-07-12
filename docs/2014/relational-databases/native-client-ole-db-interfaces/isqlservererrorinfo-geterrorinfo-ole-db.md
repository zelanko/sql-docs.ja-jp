---
title: Isqlservererrorinfo::geterrorinfo (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f33c66d8e521339573e56b78407f0bab67b4b43e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430101"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
  ポインターを返します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの SSERRORINFO 構造を含む、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの詳細。  
  
## <a name="syntax"></a>構文  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>引数  
 *ppSSErrorInfo*[out]  
 SSERRORINFO 構造体へのポインター。 メソッドが失敗したかがあるない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]については、エラーに関連付けられている、プロバイダーは、任意のメモリを割り当てられません、確実に、 *ppSSErrorInfo*引数が出力に null ポインター。  
  
 *割り当てません*[out]  
 Unicode 文字列ポインターへのポインター。 メソッドが失敗したかがあるない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]については、エラーに関連付けられている、プロバイダーは、任意のメモリを割り当てられません、確実に、*割り当てません*引数が出力に null ポインター。 解放、*割り当てません*引数と、 **imalloc::free**ブロックにメモリが割り当て済みとして、メソッドが返される SSERRORINFO 構造体の 3 つの個々 の文字列メンバーを解放します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_INVALIDARG  
 いずれか、 *ppSSErrorInfo*または*割り当てません*引数が NULL でした。  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、要求を完了するための十分なメモリを割り当てられませんでした。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コンシューマーが渡したポインターによって返される、SSERRORINFO と OLECHAR 文字列用のメモリを割り当てます。 コンシューマーを使用してこのメモリを解放する必要があります、 **imalloc::free**メソッド エラー データにアクセスする必要がなくなったときにします。  
  
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
  
|Member|説明|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージ。 によって、メッセージが返される、 **ierrorinfo::getdescription**メソッド。|  
|*pwszServer*|エラーが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|*pwszProcedure*|エラーがストアド プロシージャ内で発生している場合は、エラーが発生したストアド プロシージャの名前です。それ以外の場合は、空文字列になります。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号。 エラー番号はで返されるのと同じ、 *plNativeError*のパラメーター、 **isqlerrorinfo::getsqlinfo**メソッド。|  
|*この*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの状態。|  
|*含まれて*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの重大度。|  
|*wLineNumber*|該当する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャのエラー メッセージを生成した行です。 プロシージャが関係していない場合は、既定値 1 が使用されます。|  
  
 返される文字列内のアドレスの構造のポインターが参照、*割り当てません*引数。  
  
## <a name="see-also"></a>参照  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
