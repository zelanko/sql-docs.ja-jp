---
description: FetchOptions プロパティ (RDS)
title: FetchOptions プロパティ (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d00dd737f6b775d9d46bfb6af96a5ce76aa3a8e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439024"
---
# <a name="fetchoptions-property-rds"></a>FetchOptions プロパティ (RDS)
非同期フェッチの種類を示します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="setting-and-return-values"></a>設定と戻り値  
 次のいずれかの値を設定または返します。  
  
|定数|説明|  
|--------------|-----------------|  
|**adcFetchUpFront**|[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)のすべてのレコードは、コントロールがアプリケーションに返される前にフェッチされます。 完全な **レコードセット** がフェッチされてから、アプリケーションで何かを実行できるようになります。|  
|**adcFetchBackground**|コントロールは、レコードの最初のバッチがフェッチされるとすぐにアプリケーションに戻ることができます。 最初のバッチでフェッチされていないレコードにアクセスしようとするレコード **セット** の後続の読み取りは、探索されたレコードが実際にフェッチされるまで遅延され、その時点で制御がアプリケーションに戻ります。|  
|**adcFetchAsync**|既定値。 レコードがバックグラウンドでフェッチされている間、コントロールは直ちにアプリケーションに戻ります。 まだフェッチされていないレコードをアプリケーションが読み取ろうとすると、探索されたレコードに最も近いレコードが読み取られ、制御が直ちに返されます。これは、 **レコードセット** の現在の末尾に達したことを示します。 たとえば、 [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) を呼び出すと、現在のレコードの位置が、実際にフェッチされた最後のレコードに移動します。ただし、レコード **セット**には、それ以上のレコードが設定されます。|  
  
> [!NOTE]
>  これらの定数を使用するクライアント側の実行可能ファイルは、それぞれの宣言を提供する必要があります。 RDS ライブラリの既定のインストールフォルダーにある Adcvbs. inc. ファイルから、必要な定数宣言を切り取って貼り付けることができます。  
  
## <a name="remarks"></a>解説  
 Web アプリケーションでは、通常、 **Adcfetchasync** (既定値) を使用することをお勧めします。これは、パフォーマンスが向上するためです。 コンパイルされたクライアントアプリケーションでは、通常、 **Adcfetchbackground**を使用します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ExecuteOptions および FetchOptions プロパティの例 (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


