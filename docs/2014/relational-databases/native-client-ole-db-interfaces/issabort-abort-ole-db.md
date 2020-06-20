---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: a2055514d3ce5e2fdc9d6220a79f489fc64e9c55
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056146"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Remarks  
 中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。 サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。 クライアントが結果セットを使用しない場合、行セットを解放する前に **ISSAbort::Abort** を呼び出すと、行セットの解放が高速になります。ただし、開いているトランザクションがあり、XACT_ABORT が ON の場合、**ISSAbort::Abort** が呼び出されたときに、トランザクションがロールバックされます。  
  
 **Issabort:: Abort**が S_OK を返すと、関連付けられた**IMultipleResults**インターフェイスは使用できない状態になり、解放されるまで、すべてのメソッド呼び出し ( **IUnknown**インターフェイスによって定義されるメソッドを除く) に DB_E_CANCELED を返します。 **Abort** を呼び出す前に、**IMultipleResults** から **IRowset** を取得している場合、これも使用できない状態になり、**ISSAbort::Abort** の正常な呼び出し後にこのインターフェイスが解放されるまでは、すべてのメソッド呼び出しで DB_E_CANCELED が返されます (ただし、**IUnknown** インターフェイスと **IRowset::ReleaseRows** で定義されたメソッドは除きます)。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サーバーの XACT_ABORT 状態が ON の場合、**ISSAbort::Abort** を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに、現在のすべての暗黙的または明示的なトランザクションが終了し、ロールバックされます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
## <a name="arguments"></a>引数  
 [なし] :  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 **ISSAbort::Abort** メソッドは、バッチが取り消された場合 S_OK を、それ以外の場合 DB_E_CANTCANCEL を返します。 バッチが既に取り消されている場合は、DB_E_CANCELED を返します。  
  
 DB_E_CANCELED  
 バッチは既に取り消されています。  
  
 DB_E_CANTCANCEL  
 バッチは取り消されませんでした。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、**ISSAbort::Abort** が既に呼び出されていたために、オブジェクトがゾンビ状態になっている場合などです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
