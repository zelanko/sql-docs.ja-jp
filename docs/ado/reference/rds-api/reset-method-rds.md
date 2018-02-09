---
title: "Reset メソッド (RDS) |Microsoft ドキュメント"
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f95d5bf30a0646d3e67ae366e29794018095706a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="reset-method-rds"></a>Reset メソッド (RDS)
並べ替えまたはフィルターをクライアント側で実行**Recordset**指定の並べ替えとフィルター処理のプロパティを基にします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *value*  
 省略可。 A**ブール**値が**True** 「フィルター」現在の行セットのフィルターを適用する場合 (既定)。 **False**をフィルター処理、元の行セットで、以前のフィルター オプションを削除することを示します。  
  
## <a name="remarks"></a>解説  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md)、 [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md)、 [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)、 [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)、および[FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)プロパティは、並べ替えおよびフィルター処理でクライアント側のキャッシュ機能を提供します。 並べ替えの機能は、1 つの列の値によって、レコードを並べ替えます。 フィルターの機能には、完全中に、検索条件に基づくレコードのサブセットが表示されます。 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)はキャッシュに保持されます。 **リセット**メソッドは条件を実行し、現在の置換**Recordset** 、更新可能で**レコード セット**です。  
  
 送信されていない元のデータへの変更がある場合、**リセット**メソッドは失敗します。 まず、使用して、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)読み取り/書き込みに変更を保存するメソッド**レコード セット**、しを使用して、**リセット**並べ替えまたはレコードをフィルター処理するメソッド。  
  
 省略可能なを使用することができます、行セットに対して 1 つ以上のフィルターを実行する場合は、*ブール*引数と、**リセット**メソッドです。 次の例では、これを行う方法を示します。  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [FilterColumn、FilterCriterion、FilterValue、SortColumn、および SortDirection プロパティおよびメソッドの例をリセット (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



