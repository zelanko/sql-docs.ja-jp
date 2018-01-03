---
title: "Append メソッド (ADOX インデックス) |Microsoft ドキュメント"
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
f1_keywords: Indexes::Append
helpviewer_keywords: Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7630383843d6d057e91c4c2ed88efb2fd0e751e9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="append-method-adox-indexes"></a>Append メソッド (ADOX インデックス)
新しく追加[インデックス](../../../ado/reference/adox-api/index-object-adox.md)オブジェクトを[インデックス](../../../ado/reference/adox-api/indexes-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Index*  
 **インデックス**追加するオブジェクトまたはインデックスを作成し、追加の名前。  
  
 *[列]*  
 省略可。 A**バリアント**インデックスを作成する列の名前を指定する値。 *列*パラメーターの値に対応、[名前](../../../ado/reference/adox-api/name-property-adox.md)のプロパティ、[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトまたはオブジェクト。  
  
## <a name="remarks"></a>解説  
 *列*パラメーターは、列の名前または列名の配列を取ることができます。  
  
 プロバイダーはインデックスの作成をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [インデックスの追加メソッドの例 (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append メソッド (ADOX 列)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX グループ)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX キー)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX プロシージャ)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX ユーザー)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
