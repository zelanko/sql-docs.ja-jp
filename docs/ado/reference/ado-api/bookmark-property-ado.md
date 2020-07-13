---
title: Bookmark プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b1c27eb728c3cd368b4d2acc10609785c06514a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748619"
---
# <a name="bookmark-property-ado"></a>Bookmark プロパティ (ADO)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト内の現在のレコードを一意に識別するブックマークを示します。または、**レコードセット**オブジェクトの現在のレコードを、有効なブックマークによって識別されるレコードに設定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 有効なブックマークに評価される**バリアント**式を設定または返します。  
  
## <a name="remarks"></a>Remarks  
 **Bookmark**プロパティを使用して、現在のレコードの位置を保存し、いつでもそのレコードに戻るようにします。 ブックマークは、ブックマーク機能をサポートする**レコードセット**オブジェクトでのみ使用できます。  
  
 レコード**セット**オブジェクトを開くと、各レコードに一意のブックマークが作成されます。 現在のレコードのブックマークを保存するには、 **bookmark**プロパティの値を変数に割り当てます。 別のレコードに移動した後、いつでもそのレコードにすばやく戻るには、**レコードセット**オブジェクトの**Bookmark**プロパティをその変数の値に設定します。  
  
 ユーザーはブックマークの値を表示できない可能性があります。 また、同じレコードを参照する2つのブックマークの値が異なる可能性があるため、ブックマークを直接比較することはできません。  
  
 [Clone](../../../ado/reference/ado-api/clone-method-ado.md)メソッドを使用して**レコードセット**オブジェクトのコピーを作成する場合、元のレコードセットオブジェクトと重複した**レコードセット**オブジェクトの**Bookmark**プロパティ設定は同じであり、同じように使用できます。 ただし、同じソースまたはコマンドから作成された場合でも、異なる**レコードセット**オブジェクトのブックマークを同じように使用することはできません。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況**クライアント側の**レコードセット**オブジェクトで使用する場合、 **Bookmark**プロパティは常に使用できます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BOF、EOF、および Bookmark プロパティの例 (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF、EOF、および Bookmark プロパティの例 (VC + +)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports メソッド](../../../ado/reference/ado-api/supports-method.md)
