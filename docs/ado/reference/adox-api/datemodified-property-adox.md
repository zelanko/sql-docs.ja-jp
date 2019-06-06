---
title: DateModified プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5d0cd8a6196bdc0f933470a52dbb3567f64df05e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718923"
---
# <a name="datemodified-property-adox"></a>DateModified プロパティ (ADOX)
オブジェクトの最終更新日を示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**バリアント**変更された日付を指定する値。 値が null の場合は**DateModified**はプロバイダーによってサポートされていません。  
  
## <a name="remarks"></a>コメント  
 **DateModified**プロパティが null のオブジェクトを新たに追加します。 新しく追加した後[ビュー](../../../ado/reference/adox-api/view-object-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)、呼び出す必要があります、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)のメソッド、[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)の値を取得するコレクション、 **DateModified**プロパティ。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [DateCreated および DateModified プロパティの例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated プロパティ (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
