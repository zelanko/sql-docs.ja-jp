---
title: FilterValue プロパティ (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterValue property [ADO]
ms.assetid: 28f17186-b842-4cf9-b320-a9bb941c481b
author: rothja
ms.author: jroth
ms.openlocfilehash: 17d4585a237b2dcd32df1508aeb85b291d4d9296
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751996"
---
# <a name="filtervalue-property-rds"></a>FilterValue プロパティ (RDS)
レコードのフィルター処理に使用する値を示します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.FilterValue = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *String*  
 レコードをフィルター処理するために使用するデータ値を表す**文字列**値 ( `'Programmer'` やなど `125` )。  
  
## <a name="remarks"></a>Remarks  
 [Sortcolumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md)、 [sortcolumn](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 **filtervalue**、 [filterfilter、](../../../ado/reference/rds-api/filtercriterion-property-rds.md)および[filtervalue](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、クライアント側キャッシュでの並べ替えとフィルター処理の機能を提供します。 並べ替え機能は、1つの列の値でレコードを並べ替えます。 フィルター機能では、検索条件に基づいてレコードのサブセットが表示されますが、完全な[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [Reset](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは、条件を実行し、現在の**レコードセット**を更新可能な**レコードセット**に置き換えます。  
  
 Null 値を指定すると、型の不一致エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、Filtercolumn、Filtercolumn、SortColumn、および Sortcolumn プロパティと Reset メソッドの例 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn プロパティ (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [Filterfilterproperty (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [SortColumn プロパティ (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)






















