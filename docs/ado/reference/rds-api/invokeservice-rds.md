---
title: "InvokeService (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be188df1a61cfd398644ba42af5d32605d501919
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
オブジェクトのより高機能なバージョンで要求されたインターフェイスへのポインターを返します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
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
  
 [out]要求されたインターフェイス ポインターを受け取るポインター変数のアドレス*riid*です。 成功時に、 *ppunkMoreFunctionalInterface*パラメーターには、オブジェクトへの要求されたインターフェイス ポインターが含まれています。 オブジェクトがで指定されたインターフェイスをサポートしていない場合*riid*、 *ppunkMoreFunctionalInterface*は NULL に設定します。  
  
## <a name="return-value"></a>戻り値  
 どうかを示す HRESULT 値への呼び出し、 **InvokeService**メソッドが正常に完了しました。  
  
## <a name="remarks"></a>解説  
 RDS カーソル エンジンの実装の**InvokeService**入力行セット (または複数の結果オブジェクト) を受け取り、入力行セットからカーソル エンジンを追加およびそれ自体でポインターを返します。  
  
## <a name="applies-to"></a>適用対象  
 [IRDSService インターフェイス (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>参照  
 [RDS メソッド](../../../ado/reference/rds-api/rds-methods.md)


