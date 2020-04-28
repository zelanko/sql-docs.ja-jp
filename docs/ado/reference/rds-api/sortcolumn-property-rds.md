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
ms.openlocfilehash: b5a9c3f9f50968f3b5e8085052917397bcd90226
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963390"
---
# <a name="sortcolumn-property-rds"></a>SortColumn プロパティ (RDS)
レコードを並べ替える列を指定します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *String*  
 レコードの並べ替えに使用する列の名前または別名を表す**文字列**値。  
  
## <a name="remarks"></a>Remarks  
 **Sortcolumn**、 [sortcolumn](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 [filtervalue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 [filterfilter、](../../../ado/reference/rds-api/filtercriterion-property-rds.md)および[filtervalue](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、クライアント側キャッシュでの並べ替えとフィルター処理の機能を提供します。 並べ替え機能は、1つの列の値でレコードを並べ替えます。 フィルター機能では、検索条件に基づいてレコードのサブセットが表示されますが、完全な[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [Reset](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは、条件を実行し、現在の**レコードセット**を更新可能な**レコードセット**に置き換えます。  
  
 **レコードセット**を並べ替えるには、保留中の変更を最初に保存する必要があります。 RDS を使用している場合 **。DataControl**では、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)メソッドを使用できます。 たとえば、RDS の場合など**です。DataControl**の名前は ADC1 で、コードは`ADC1.SubmitChanges`になります。 ADO**レコードセット**を使用している場合は、その[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドを使用できます。 [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)メソッドを使用して作成された**レコードセット**オブジェクトには、 **UpdateBatch**を使用することをお勧めします。 たとえば、コードはまたは`myRS.UpdateBatch` `ADC1.Recordset.UpdateBatch`のようになります。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、Filtercolumn、Filtercolumn、SortColumn、および Sortcolumn プロパティと Reset メソッドの例 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort プロパティ](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





