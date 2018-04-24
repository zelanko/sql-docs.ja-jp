---
title: ReadyState プロパティ (RDS) |Microsoft ドキュメント
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 78a5b98cdf0eff5cb84165e8fd38b58c2b87e58a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="readystate-property-rds"></a>ReadyState プロパティ (RDS)
進行状況を示す、 [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトへのデータが取得されてその[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または値は次のいずれかを返します。  
  
|値|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|現在のクエリが実行中で、行が取得されていません。 **DataControl**オブジェクトの**Recordset**は使用されません。|  
|**adcReadyStateInteractive**|現在のクエリによって取得される行の初期セットが格納されている、 **DataControl**オブジェクトの**Recordset**し、使用可能な。 残りの行がまだフェッチされています。|  
|**adcReadyStateComplete**|現在のクエリによって取得されるすべての行が格納されている、 **DataControl**オブジェクトの**Recordset**し、使用可能な。<br /><br /> この状態が、エラーのため、操作が中止された場合、または場合にも存在、 **Recordset**オブジェクトが初期化されていません。|  
  
> [!NOTE]
>  これらの定数を使用するクライアント側実行可能ファイルは、それらの宣言をする必要があります。 RDS ライブラリの既定のインストール フォルダーにあるファイル Adcvbs.inc から、使用する定数の宣言を貼り付けるを切り取ってことができます。  
  
## <a name="remarks"></a>解説  
 使用して、 [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md)変更を監視するイベント、 **ReadyState**非同期クエリ操作中にプロパティです。 これは、プロパティの値を定期的に確認するよりも効率的です。  
  
 非同期の操作中にエラーが発生した場合、 **ReadyState**プロパティに対する変更を**adcReadyStateComplete**、[状態](../../../ado/reference/ado-api/state-property-ado.md)からプロパティが変更された**adStateExecuting**に**取得のみ**、および**レコード セット**オブジェクト[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティまま*何も行われません*.  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ReadyState プロパティの例 (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [ExecuteOptions プロパティ (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


