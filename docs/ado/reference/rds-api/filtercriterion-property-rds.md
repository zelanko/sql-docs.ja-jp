---
title: FilterCriterion プロパティ (RDS) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterCriterion property [RDS]
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 015cf292a4b9cd0720e379b83d5fcf254c841c8f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288258"
---
# <a name="filtercriterion-property-rds"></a>FilterCriterion プロパティ (RDS)
フィルター選択値を使用する評価演算子を示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *文字列*  
 A**文字列**の評価の演算子を指定する値、 [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)レコードにします。 次のいずれかを指定できます: <、 \<=、>、> =、=、または <> です。  
  
## <a name="remarks"></a>コメント  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md)、 [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 **FilterCriterion**、および[FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、並べ替えおよびフィルター処理でクライアント側のキャッシュ機能を提供します。 並べ替えの機能は、1 つの列の値によって、レコードを並べ替えます。 フィルターの機能は、完全な検索条件に基づくレコードのサブセットを表示[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 [リセット](../../../ado/reference/rds-api/reset-method-rds.md)メソッドは条件を実行し、現在の置換**Recordset** 、更新可能で**レコード セット**です。  
  
 "! ="演算子が無効の**FilterCriterion**。 代わりに、"<>"を使用します。  
  
 フィルターと並べ替えの両方のプロパティを設定しを呼び出すかどうか、**リセット**メソッド、行セットがフィルター選択された最初およびに並べ替えられます。 昇順の並べ替え、null 値は、上部;降順の並べ替え、null 値は、下部にある (既定の動作は、昇順)。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、FilterCriterion、FilterValue、SortColumn、および SortDirection プロパティおよびメソッドの例をリセット (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn プロパティ (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterValue プロパティ (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [SortColumn プロパティ (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


