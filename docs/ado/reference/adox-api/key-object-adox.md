---
title: キーのオブジェクト (ADOX) |Microsoft ドキュメント
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
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05863d8227f2f0dddc6b7a44c60951fe3f8471be
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286841"
---
# <a name="key-object-adox"></a>キー オブジェクト (ADOX)
データベース テーブルから、外部キー、または一意のキー フィールドを表します。  
  
## <a name="remarks"></a>コメント  
 次のコードが新たに作成**キー**:  
  
```  
Dim obj As New Key  
```  
  
 プロパティのコレクションと、**キー**オブジェクトをすることができます。  
  
-   キーを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   キーが、外部キー、または一意にするかどうかを判断する、[型](../../../ado/reference/adox-api/type-property-key-adox.md)プロパティです。  
  
-   データベースのキーの列へのアクセス、[列](../../../ado/reference/adox-api/columns-collection-adox.md)コレクション。  
  
-   関連するテーブルの名前を指定、 [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md)プロパティです。  
  
-   削除または付きの主キーの更新プログラムで実行されるアクションを判断する、 [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md)と[UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md)プロパティです。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Key オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
