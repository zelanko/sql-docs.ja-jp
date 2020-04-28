---
title: Append メソッド (ADOX Columns) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6493157c00e5a71c7c2f085191231bb33bb5279a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967328"
---
# <a name="append-method-adox-columns"></a>Append メソッド (ADOX Columns)
[Columns](../../../ado/reference/adox-api/columns-collection-adox.md)コレクションに新しい[Column](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
 追加する**列**オブジェクト、または作成して追加する列の名前。  
  
 *Type*  
 任意。 列のデータ型を指定する**Long**型の値です。 *Type*パラメーターは、 **Column**オブジェクトの[type](../../../ado/reference/adox-api/type-property-column-adox.md)プロパティに対応しています。  
  
 *DefinedSize*  
 任意。 列のサイズを指定する**Long 型**の値です。 指定された*サイズ*のパラメーターは、 **Column**オブジェクトの "指定された[サイズ](../../../ado/reference/adox-api/definedsize-property-adox.md)" プロパティに対応します。  
  
> [!NOTE]
>  [テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)コレクションに既に追加されている[テーブル](../../../ado/reference/adox-api/table-object-adox.md)**に列が**存在しない場合、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)の**Columns**コレクションに**列**を追加すると、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Indexes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX Keys)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX Procedures)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
