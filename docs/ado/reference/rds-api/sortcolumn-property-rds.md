---
title: SortColumn プロパティ (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 370bec12ac65e78c2eb104c3e5fe25d4fc8b434a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763360"
---
# <a name="sortcolumn-property-rds"></a>SortColumn プロパティ (RDS)
レコードの並べ替え列を示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *文字列*  
 A**文字列**名前またはレコードの並べ替えに使用する列の別名を表す値です。  
  
## <a name="remarks"></a>Remarks  
 **SortColumn**、 [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)、および[FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、並べ替えおよびフィルター処理、クライアント側キャッシュの機能を提供します。 並べ替えの機能は、1 つの列の値によってレコードを並べ替えます。 フィルター機能は、完全な検索条件に基づくレコードのサブセットを表示[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [リセット](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは、条件を実行し、現在の置換**Recordset**で更新可能な**レコード セット**します。  
  
 並べ替えに使用する、 **Recordset**、保留中の変更を最初に保存する必要があります。 使用する場合、 **rds.DataControl**、使用することができます、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)メソッド。 たとえば場合、 **rds.DataControl**は ADC1 をという名前に、`ADC1.SubmitChanges`します。 ADO を使用している場合**Recordset**、使用することができます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド。 使用して**UpdateBatch** 、推奨される方法は、 **Recordset**で作成されるオブジェクト、 [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)メソッド。 たとえば、コードは`myRS.UpdateBatch`または`ADC1.Recordset.UpdateBatch`します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>関連項目  
 [FilterColumn、FilterCriterion、FilterValue、SortColumn、SortDirection プロパティおよび Reset メソッドの例 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort プロパティ](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





