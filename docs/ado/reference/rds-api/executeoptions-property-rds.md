---
title: ExecuteOptions プロパティ (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2ae55ec1fccbd491854fb8bff2daa215d38b20ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964185"
---
# <a name="executeoptions-property-rds"></a>ExecuteOptions プロパティ (RDS)
非同期実行が有効かどうかを示します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 次のいずれかの値を設定または返します。  
  
|常時|[説明]|  
|--------------|-----------------|  
|**adcExecSync**|[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)の次の更新を同期的に実行します。|  
|**adcExecAsync**|既定。 **レコードセット**の次の更新を非同期的に実行します。|  
  
> [!NOTE]
>  これらの定数を使用する実行可能ファイルはそれぞれ、それぞれの宣言を提供する必要があります。 RDS ライブラリの既定のインストールフォルダーにある Adcvbs. inc. ファイルから、必要な定数宣言を切り取って貼り付けることができます。  
  
## <a name="remarks"></a>解説  
 **Executeoptions**が**Adcexecasync**に設定されている場合、RDS で次の**更新**呼び出しが非同期に実行され[ます。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**レコードセット**。  
  
 RDS を変更する可能性のある別の非同期操作中に[Reset](../../../ado/reference/rds-api/reset-method-rds.md)、 [Refresh](../../../ado/reference/rds-api/refresh-method-rds.md)、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)、 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)、または[レコードセット](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)を呼び出そうとした場合[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**レコードセット**が実行中であるため、エラーが発生します。  
  
 非同期操作中にエラーが発生した場合は、 **RDS.DataControl**オブジェクトの[ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)値が**Adcreadystateloaded**から**adcReadyStateComplete**に変更されましたが、**レコードセット**プロパティの値は*何も*保持されません。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ExecuteOptions および FetchOptions プロパティの例 (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


