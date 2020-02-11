---
title: SortDirection プロパティ (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28f0e247c29673fe4dfec507794ad8977b51fcc1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963414"
---
# <a name="sortdirection-property-rds"></a>SortDirection プロパティ (RDS)
並べ替え順序が昇順と降順のどちらであるかを示します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *Value*  
 **ブール**値。 **True**に設定されている場合、並べ替えの方向が昇順であることを示します。 **False**は降順を示します。  
  
## <a name="remarks"></a>解説  
 [Sortcolumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md)、 **sortcolumn**、 [filtervalue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 [filterfilter、](../../../ado/reference/rds-api/filtercriterion-property-rds.md)および[filtervalue](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、クライアント側キャッシュでの並べ替えとフィルター処理の機能を提供します。 並べ替え機能では、1つの列の値を使用してレコードが順序付けされます。 フィルター機能では、検索条件に基づいてレコードのサブセットが表示されますが、完全な[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [Reset](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは、条件を実行し、現在の**レコードセット**を更新可能な**レコードセット**に置き換えます。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、Filtercolumn、Filtercolumn、SortColumn、および Sortcolumn プロパティと Reset メソッドの例 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort プロパティ](../../../ado/reference/ado-api/sort-property.md)   
 [SortColumn プロパティ (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


