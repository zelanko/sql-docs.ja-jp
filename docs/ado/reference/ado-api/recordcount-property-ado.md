---
title: "RecordCount プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 92faeb5d2ec0b62c03292f71e0299c779e362478
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="recordcount-property-ado"></a>RecordCount プロパティ (ADO)
内のレコードの数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**内のレコードの数を示す値、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **RecordCount**でどれくらいのレコードを検索するプロパティには、 **Recordset**オブジェクト。 プロパティは、ADO レコードの数を判断できない場合や、プロバイダーまたはカーソルの種類がサポートされていない場合に-1 を返します**RecordCount**です。 読み取り、 **RecordCount**プロパティに、閉じられた**Recordset**エラーが発生します。  
  
 場合、 **Recordset**オブジェクトのおおよその位置をサポートしているまたはブックマーク つまり、 **(adApproxPosition) をサポートしています**または**(adBookmark) をサポートしています**、それぞれ、返す**True**ビルダー この値は内のレコードの正確な数になります、 **Recordset**かどうかが完全に作成済みに関係なく、します。 場合、 **Recordset**オブジェクトは、おおよその位置をサポートしていない、すべてのレコードが取得して返す正確なカウントする必要があるために、このプロパティは、リソースを消耗にあります**RecordCount**値。  
  
> [!NOTE]
>  SQLOLEDB プロバイダーがサーバー側カーソルが使用される場合でも、返されるすべてのレコードをフェッチ ADO 2.8 およびそれ以前のバージョン、 **True**両方の**サポート (adApproxPosition)**と**サポート (adBookmark)**です。  
  
 カーソルの種類、 **Recordset**オブジェクトは、レコードの数を決定できるかどうかに影響します。 **RecordCount**プロパティは、順方向専用カーソル以外の場合は、静的な実際の数またはキーセット カーソル; し、-1 の場合は-1 または動的カーソルの場合は、データ ソースによって実際の数を返します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [フィルターおよび RecordCount のプロパティの例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [フィルターおよび RecordCount のプロパティの例 (vc++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
