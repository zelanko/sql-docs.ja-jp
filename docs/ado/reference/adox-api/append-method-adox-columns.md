---
title: Append メソッド (ADOX 列) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e53965f9a8c5602459a08f5c47e5719741bb648
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-columns"></a>Append メソッド (ADOX 列)
新しく追加[列](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトを[列](../../../ado/reference/adox-api/columns-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
 **列**追加するオブジェクトまたは列を作成し、追加の名前。  
  
 *型*  
 省略可。 A**長い**列のデータ型を指定する値。 *型*パラメーターに対応、[型](../../../ado/reference/adox-api/type-property-column-adox.md)のプロパティ、**列**オブジェクト。  
  
 *DefinedSize*  
 省略可。 A**長い**列のサイズを指定する値。 *DefinedSize*パラメーターに対応、 [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md)のプロパティ、**列**オブジェクト。  
  
> [!NOTE]
>  追加するときにエラーが発生、**列**を**列**のコレクション、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)場合、**列**に存在しません[テーブル](../../../ado/reference/adox-api/table-object-adox.md)に既に追加されて、[テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)コレクション。  
  
## <a name="applies-to"></a>適用対象  
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [列とテーブル名プロパティの例 (VB) のメソッドを追加します。](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append メソッド (ADOX グループ)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX インデックス)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX キー)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX プロシージャ)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX ユーザー)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
