---
title: "FetchOptions プロパティ (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ca6ede3ae154cbb3b6e13038185e4a54a466009
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="fetchoptions-property-rds"></a>FetchOptions プロパティ (RDS)
非同期フェッチの型を示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="setting-and-return-values"></a>設定して、戻り値  
 設定または値は次のいずれかを返します。  
  
|定数|Description|  
|--------------|-----------------|  
|**adcFetchUpFront**|すべてのレコード、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)コントロールは、アプリケーションに返される前にフェッチされます。 完全な**Recordset**を前に、アプリケーションとは何も操作をフェッチします。|  
|**adcFetchBackground**|コントロールは、レコードの最初のバッチがフェッチされるとすぐにアプリケーションに返すことができます。 それ以降の読み取り、 **Recordset**最初のバッチでフェッチされなかったレコードへのアクセスの試行は、要求されたレコードが実際にフェッチされるまで遅延されます、アプリケーションに制御が戻る時点であります。|  
|**adcFetchAsync**|既定値です。 コントロールは、レコードがバック グラウンドでフェッチ中にアプリケーションにすぐに返します。 要求されたレコードに最も近いレコードが読み取られ、コントロールすぐに戻り、ことを示す場合は、アプリケーションがフェッチされていないレコードを読み取るしようとするの現在の末尾、**レコード セット**に達しています。 呼び出しなど、 [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)はより多くのレコードは引き続きを設定する場合でも、実際にフェッチされた最後のレコードに、現在のレコードの位置を移動、 **Recordset**です。|  
  
> [!NOTE]
>  これらの定数を使用するクライアント側実行可能ファイルは、それらの宣言をする必要があります。 RDS ライブラリの既定のインストール フォルダーにあるファイル Adcvbs.inc から、使用する定数の宣言を貼り付けるを切り取ってことができます。  
  
## <a name="remarks"></a>解説  
 Web アプリケーションでは通常使用する**adcFetchAsync** (既定値) の場合は、パフォーマンス向上を提供するためです。 コンパイル済みのクライアント アプリケーションでは通常使用する**adcFetchBackground**です。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ExecuteOptions と FetchOptions プロパティの例 (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)



