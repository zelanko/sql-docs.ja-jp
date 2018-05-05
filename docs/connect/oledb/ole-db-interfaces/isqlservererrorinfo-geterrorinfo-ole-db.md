---
title: Isqlservererrorinfo::geterrorinfo (OLE DB) |Microsoft ドキュメント
description: ISQLServerErrorInfo::GetErrorInfo (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9aabd708d0fdd99b96667129ab3dc3eb90093a51
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB 用のドライバーを含む SQL Server の SSERRORINFO 構造体へのポインターを返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]エラーの詳細。  
  
 SQL Server の OLE DB ドライバーでは定義、 **ISQLServerErrorInfo**エラー インターフェイスです。 このインターフェイスは詳細情報を返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]重大度や状態などのエラーです。  

  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>引数  
 *ppSSErrorInfo*[out]  
 SSERRORINFO 構造体へのポインター。 メソッドが失敗したか、または場合ありません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]については、エラーに関連付けられている、プロバイダーは、任意のメモリを割り当てられません、確実に、 *ppSSErrorInfo*引数が出力に null ポインターです。  
  
 *割り当てません*[out]  
 Unicode 文字列ポインターへのポインター。 メソッドが失敗したか、または場合ありません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]については、エラーに関連付けられている、プロバイダーは、任意のメモリを割り当てられません、確実に、*割り当てません*引数が出力に null ポインターです。 解放、*割り当てません*引数と、 **imalloc::free**ブロックでメモリが割り当て済みとしてメソッドが返された SSERRORINFO 構造体の 3 つの文字列の個々 のメンバーを解放します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_INVALIDARG  
 いずれか、 *ppSSErrorInfo*または*割り当てません*引数が NULL です。  
  
 E_OUTOFMEMORY  
 SQL Server の OLE DB Driver は、要求を完了するための十分なメモリを割り当てられませんでした。  
  
## <a name="remarks"></a>解説  
 SQL Server の OLE DB Driver は、SSERRORINFO 文字列と OLECHAR 文字列、コンシューマーが渡したポインターを通じて返されるのメモリを割り当てます。 コンシューマーを使用してこのメモリを解放する必要があります、 **imalloc::free**メソッド エラー データにアクセスする必要がなくなったときにします。  
  
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
  
|メンバー|Description|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエラー メッセージ。 を介して、メッセージが返されます、 **ierrorinfo::getdescription**メソッドです。|  
|*pwszServer*|エラーが発生した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|*pwszProcedure*|エラーがストアド プロシージャ内で発生している場合は、エラーが発生したストアド プロシージャの名前です。それ以外の場合は、空文字列になります。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエラー番号。 エラー番号はで返されるものと同じ、 *plNativeError*のパラメーター、 **isqlerrorinfo::getsqlinfo**メソッドです。|  
|*この*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エラーの状態。|  
|*あり*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エラーの重大度。|  
|*wLineNumber*|該当する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャのエラー メッセージを生成した行です。 プロシージャが関係していない場合は、既定値 1 が使用されます。|  
  
 構造のポインターで返される文字列内のアドレスを参照する、*割り当てません*引数。  
  
## <a name="see-also"></a>参照  
 [ISQLServerErrorInfo (&) #40";"OLE DB"&"#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR と #40 です。TRANSACT-SQL と #41 です。](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
