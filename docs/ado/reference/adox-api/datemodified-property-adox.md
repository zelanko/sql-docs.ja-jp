---
title: "DateModified プロパティ (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords: DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e334d9c316b8655b475f24554e3e3f6843bd884
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="datemodified-property-adox"></a>DateModified プロパティ (ADOX)
オブジェクトが最後に変更された日付を示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**バリアント**変更された日付を指定する値。 値が null の場合は**DateModified**プロバイダーでサポートされていません。  
  
## <a name="remarks"></a>解説  
 **DateModified**プロパティが null のオブジェクトを新たに追加します。 新しく追加した後[ビュー](../../../ado/reference/adox-api/view-object-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)、呼び出す必要があります、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)のメソッド、[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)の値を取得するコレクション、 **DateModified**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [作成日時と最終更新日時プロパティの例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated プロパティ (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
