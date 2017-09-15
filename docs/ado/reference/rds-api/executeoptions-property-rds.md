---
title: "ExecuteOptions プロパティ (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 29d46a26f7e4a80ae7a22954f388597552a5fb86
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executeoptions-property-rds"></a>ExecuteOptions プロパティ (RDS)
非同期の実行が有効になっているかどうかを示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または値は次のいずれかを返します。  
  
|定数|Description|  
|--------------|-----------------|  
|**adcExecSync**|次の更新を実行、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)同期的に処理します。|  
|**adcExecAsync**|既定値です。 次の更新の実行、 **Recordset**非同期的にします。|  
  
> [!NOTE]
>  これらの定数を使用する各実行可能ファイルは、それらの宣言をする必要があります。 RDS ライブラリの既定のインストール フォルダーにあるファイル Adcvbs.inc から使用する定数の宣言を貼り付けるを切り取ってことができます。  
  
## <a name="remarks"></a>解説  
 場合**ExecuteOptions**に設定されている**adcExecAsync**、非同期的に実行し、実行、次へ、**更新**でを呼び出す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**Recordset**です。  
  
 呼び出すしようとすると[リセット](../../../ado/reference/rds-api/reset-method-rds.md)、[更新](../../../ado/reference/rds-api/refresh-method-rds.md)、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)、[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)、または[Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)変わる可能性がある別の非同期操作中に、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**Recordset**実行すると、エラーが発生します。  
  
 非同期の操作中にエラーが発生した場合、 **.rds ですDataControl**オブジェクトの[ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)値から変更**adcReadyStateLoaded**に**adcReadyStateComplete**、および**レコード セット**プロパティの値のまま*Nothing*です。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ExecuteOptions と FetchOptions プロパティの例 (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)



