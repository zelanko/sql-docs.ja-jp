---
title: BOF、EOF プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1941b22639091d673bb687c3ae8b2d9ea1fdf063
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="bof-eof-properties-ado"></a>BOF、EOF プロパティ (ADO)
-   **BOF**の最初のレコードの前に、現在のレコードの位置があることを示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
-   **EOF**後の最後のレコード、現在のレコードの位置にあることを示します、 **Recordset**オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 **BOF**と**EOF**プロパティの戻り値**ブール**値。  
  
## <a name="remarks"></a>解説  
 使用して、 **BOF**と**EOF**プロパティを確認するかどうか、**レコード セット**オブジェクトには、レコードまたはかどうかを越えているの制限が含まれています、**レコード セット**オブジェクトのレコード間を移動するとします。  
  
 **BOF**プロパティから返される**True** (-1) 場合は、最初のレコードの前に、現在のレコードの位置と**False** (0)、現在のレコードの位置は 1 つ目以降の場合レコードです。  
  
 **EOF**プロパティから返される**True**場合、現在のレコードの位置は最後のレコードと**False**場合は、現在のレコードの位置、または最後のレコードの前にします。  
  
 どちらの場合、 **BOF**または**EOF**プロパティは**True**、現在のレコードが存在しません。  
  
 開く場合、 **Recordset** 、レコードが含まれていないオブジェクト、 **BOF**と**EOF**プロパティに設定されます**True** (を参照してください、 [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)プロパティのこの状態の詳細については、 **Recordset**)。 開くと、 **Recordset**には、少なくとも 1 つのレコード、最初のレコードを格納しているオブジェクトは、現在のレコードと**BOF**と**EOF**プロパティは、 **False**.  
  
 最後の残りのレコードを削除する場合、 **Recordset**オブジェクト、 **BOF**と**EOF**プロパティが残る可能性がある**False**するまで現在のレコードの位置を変更しようとしてください。  
  
 このテーブルを表示します**移動**のさまざまな組み合わせでメソッドが許可される、 **BOF**と**EOF**プロパティです。  
  
||MoveFirst、<br /><br /> MoveLast|MovePrevious、<br /><br /> < 0 を移動します。|0 を移動します。|MoveNext、<br /><br /> > 0 を移動します。|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF**=**True**、 **EOF**=**False**|Allowed|[エラー]|[エラー]|Allowed|  
|**BOF**=**False**、 **EOF**=**は True。**|Allowed|Allowed|[エラー]|[エラー]|  
|両方**は True。**|[エラー]|[エラー]|[エラー]|[エラー]|  
|両方**False**|Allowed|Allowed|Allowed|Allowed|  
  
 許可、**移動**メソッドとは限りませんのメソッドが正常にレコードを見つける以外の場合は、指定したその呼び出しに過ぎません**移動**メソッドはエラーを生成しません。  
  
 次の表は、処理、 **BOF**と**EOF**さまざまなを呼び出すときに、プロパティ設定**移動**メソッドだが、レコードを正常に配置することです。  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**、 **MoveLast**|設定**は True。**|設定**は True。**|  
|**移動**0|変更なし|変更なし|  
|**MovePrevious**、**移動**< 0|設定**は True。**|変更なし|  
|**MoveNext**、**移動**> 0|変更なし|設定**は True。**|  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BOF、EOF、およびブックマークのプロパティの例 (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF、EOF、およびブックマークのプロパティの例 (vc++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
