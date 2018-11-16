---
title: InvokeService (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efcb67792eed98caebd541ab7dab3a3fef4cd626
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606862"
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
高機能なバージョンのオブジェクトで要求されたインターフェイスへのポインターを返します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>パラメーター  
 *riid*  
  
 [in]要求されているインターフェイスの識別子。  
  
 *punkNotSoFunctionalInterface*  
  
 [in]低機能のソース オブジェクト。  
  
 *ppunkMoreFunctionalInterface*  
  
 [out]要求されたインターフェイス ポインターを受け取るポインター変数のアドレス*riid*します。 成功時に、 *ppunkMoreFunctionalInterface*パラメーターには、オブジェクトへの要求されたインターフェイス ポインターが含まれています。 オブジェクトがで指定されたインターフェイスをサポートしていない場合*riid*、 *ppunkMoreFunctionalInterface* NULL に設定されます。  
  
## <a name="return-value"></a>戻り値  
 場合を示す HRESULT 値を呼び出し、 **InvokeService**メソッドが正常に完了しました。  
  
## <a name="remarks"></a>コメント  
 RDS カーソル エンジンの実装の**InvokeService**入力行セット (または複数の結果オブジェクト) を受け取り、入力の行セットからカーソル エンジンを設定します。 および自体にポインターを返します。  
  
## <a name="applies-to"></a>適用対象  
 [IRDSService インターフェイス (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>参照  
 [RDS メソッド](../../../ado/reference/rds-api/rds-methods.md)


