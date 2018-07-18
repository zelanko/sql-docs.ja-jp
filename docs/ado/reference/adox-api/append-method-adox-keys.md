---
title: Append メソッド (ADOX キー) |Microsoft ドキュメント
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
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eaef312977613409453dfa1d876674d6b95c927
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284821"
---
# <a name="append-method-adox-keys"></a>Append メソッド (ADOX キー)
新しく追加[キー](../../../ado/reference/adox-api/key-object-adox.md)オブジェクトを[キー](../../../ado/reference/adox-api/keys-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *[キー]*  
 **キー**追加するオブジェクトまたはキーを作成し、追加の名前。  
  
 *KeyType*  
 任意。 A**長い**キーの種類を指定する値。 *キー*パラメーターに対応、[型](../../../ado/reference/adox-api/type-property-key-adox.md)のプロパティ、**キー**オブジェクト。  
  
 *列*  
 任意。 A**文字列**インデックスを作成するのには、列の名前を指定する値。 *列*パラメーターの値に対応、[名前](../../../ado/reference/adox-api/name-property-adox.md)のプロパティ、[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクト。  
  
 *RelatedTable*  
 任意。 A**文字列**関連テーブルの名前を指定する値。 *RelatedTable*パラメーターの値に対応、**名前**のプロパティ、[テーブル](../../../ado/reference/adox-api/table-object-adox.md)オブジェクト。  
  
 *RelatedColumn*  
 任意。 A**文字列**外部キーの関連する列の名前を指定する値。 *RelatedColumn*パラメーターの値に対応、**名前**のプロパティ、[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクト。  
  
## <a name="remarks"></a>コメント  
 *列*パラメーターは、列の名前または列名の配列を取ることができます。  
  
## <a name="applies-to"></a>適用対象  
 [Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append メソッド (ADOX 列)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX グループ)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX インデックス)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX プロシージャ)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX ユーザー)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
