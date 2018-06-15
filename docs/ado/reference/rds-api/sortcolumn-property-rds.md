---
title: SortColumn プロパティ (RDS) |Microsoft ドキュメント
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5253e7ad569413fc22e4a8d0ab04c8b7c403410
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288491"
---
# <a name="sortcolumn-property-rds"></a>SortColumn プロパティ (RDS)
レコードの並べ替えにする列を示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *文字列*  
 A**文字列**名前またはレコードの並べ替えに使用する列の別名を表す値です。  
  
## <a name="remarks"></a>コメント  
 **SortColumn**、 [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)、および[FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、並べ替えおよびフィルター処理でクライアント側のキャッシュ機能を提供します。 並べ替えの機能は、1 つの列の値によって、レコードを並べ替えます。 フィルターの機能は、完全な検索条件に基づくレコードのサブセットを表示[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [リセット](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは条件を実行し、現在の置換**Recordset** 、更新可能で**レコード セット**です。  
  
 並べ替えに使用する、 **Recordset**、保留中の変更を最初に保存する必要があります。 使用している場合、 **.rds ですDataControl**、使用することができます、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)メソッドです。 たとえば場合、 **.rds ですDataControl**は ADC1 をという名前には、コードになります`ADC1.SubmitChanges`です。 ADO を使用している場合**Recordset**、使用することができます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドです。 使用して**UpdateBatch**の方法はお勧め**Recordset**で作成されるオブジェクト、 [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)メソッドです。 たとえば、コードがある可能性があります`myRS.UpdateBatch`または`ADC1.Recordset.UpdateBatch`です。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、FilterCriterion、FilterValue、SortColumn、および SortDirection プロパティおよびメソッドの例をリセット (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [並べ替えのプロパティ](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





