---
title: Bookmark プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59cc184403fff8b152ee7eabbdf823abd6c3d4bc
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="bookmark-property-ado"></a>Bookmark プロパティ (ADO)
ブックマークの現在のレコードを一意に識別することを示します、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトまたは現在のレコードを設定、**レコード セット**レコードの有効なブックマークによって識別されるオブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バリアント**有効なブックマークに評価される式。  
  
## <a name="remarks"></a>解説  
 使用して、**ブックマーク**プロパティを現在のレコードの位置を保存し、いつでもそのレコードに戻ります。 のみ使用可能なブックマークは**Recordset**ブックマーク機能をサポートするオブジェクト。  
  
 開くと、 **Recordset**オブジェクトの一意のブックマークが各レコード。 現在のレコードのブックマークを保存するには、値を割り当てる、**ブックマーク**変数へのプロパティです。 戻るにはすぐにそのレコードにいつでも別のレコードに移動した後、次のように設定します。、 **Recordset**オブジェクトの**ブックマーク**プロパティをその変数の値にします。  
  
 ユーザーはできない、ブックマークの値を表示することがあります。 また、ユーザーには、同じレコードを参照する 2 つのブックマークに異なる値可能性があるために、直接比較するブックマークは限りません。  
  
 使用する場合、[クローン](../../../ado/reference/ado-api/clone-method-ado.md)のコピーを作成する方法、 **Recordset**オブジェクト、**ブックマーク**元と重複するプロパティの設定**レコード セット**オブジェクトが同じあり、置き換えて使用できます。 ただし、別のブックマークを使用することはできません**Recordset**同じソースまたはコマンドから作成された場合でも、同じ意味で、オブジェクトです。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**レコード セット**オブジェクト、**ブックマーク**プロパティは、常に使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BOF、EOF、およびブックマークのプロパティの例 (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF、EOF、およびブックマークのプロパティの例 (vc++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports メソッド](../../../ado/reference/ado-api/supports-method.md)
