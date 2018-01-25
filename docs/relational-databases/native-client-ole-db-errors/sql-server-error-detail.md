---
title: "SQL Server エラーの詳細 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-errors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: "28"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc92bf42168e381a7725e2480c9d4e9ba0521b0a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-error-detail"></a>SQL Server エラーの詳細
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのプロバイダー固有のエラー インターフェイス定義[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)です。 このインターフェイスにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの詳細が返されるので、コマンドの実行や行セットの操作が失敗したときに役立ちます。  
  
 アクセスを取得する 2 つの方法がある**ISQLServerErrorInfo**インターフェイスです。  
  
 コンシューマーは、呼び出すことがあります**ierrorrecords:**を取得する、 **ISQLServerErrorInfo**ポインター、次のコード サンプルで示すようにします。 (を入手する必要はありません**ISQLErrorInfo**)。両方**ISQLErrorInfo**と**ISQLServerErrorInfo**でカスタムの OLE DB エラー オブジェクトを**ISQLServerErrorInfo**プロシージャ名や行番号などの詳細情報を含む、サーバー エラーの情報を取得するインターフェイスです。  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 取得する別の方法、 **ISQLServerErrorInfo**ポインターが呼び出されて、 **QueryInterface**メソッドを既に取得した**ISQLErrorInfo**ポインター。 ため**ISQLServerErrorInfo**から利用できる情報のスーパー セットが含まれています**ISQLErrorInfo**に直接移動するが合理的**ISQLServerErrorInfo**を通じて**GetCustomerErrorObject**です。  
  
 **ISQLServerErrorInfo**インターフェイスが 1 つのメンバー関数を公開[isqlservererrorinfo::geterrorinfo](../../relational-databases/native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)です。 この関数では、SSERRORINFO 構造体へのポインターと文字列バッファーへのポインターが返されます。 両方のポインターが参照するメモリを使用して、コンシューマーの割り当てを解除する必要があります、 **imalloc::free**メソッドです。  
  
 コンシューマーでは SSERRORINFO 構造体のメンバーが次のように解釈されます。  
  
|メンバー|Description|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー メッセージです。 返される文字列と同じ**ierrorinfo::getdescription**です。|  
|*pwszServer*|セッションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|*pwszProcedure*|該当する場合は、エラーが発生したプロシージャの名前です。 該当しない場合は空文字列です。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ エラー番号です。 返される値と同一で、 *plNativeError*のパラメーター **isqlerrorinfo::getsqlinfo**です。|  
|*この*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー メッセージの状態です。|  
|*あり*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー メッセージの重大度です。|  
|*wLineNumber*|該当する場合は、ストアド プロシージャでエラーが発生した行番号です。|  
  
## <a name="see-also"></a>参照  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)   
 [RAISERROR と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
