---
title: 作成日時プロパティ (ADOX) |Microsoft ドキュメント
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
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c7504f93093291e2a8863367a5f05b18d9214ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datecreated-property-adox"></a>作成日時プロパティ (ADOX)
オブジェクトが作成された日付を示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**バリアント**作成された日付を指定する値。 値が null の場合は**DateCreated**プロバイダーでサポートされていません。  
  
## <a name="remarks"></a>解説  
 **DateCreated**プロパティが null のオブジェクトを新たに追加します。 新しく追加した後[ビュー](../../../ado/reference/adox-api/view-object-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)、呼び出す必要があります、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)のメソッド、[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)の値を取得するコレクション、 **DateCreated**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [作成日時と最終更新日時プロパティの例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified プロパティ (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
