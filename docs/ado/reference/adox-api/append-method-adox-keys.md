---
title: Append メソッド (ADOX Keys) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd66edb75bec4f4b7e35c53c9ebeabd9b3c75d83
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967290"
---
# <a name="append-method-adox-keys"></a>Append メソッド (ADOX Keys)
新しい[キー](../../../ado/reference/adox-api/key-object-adox.md)オブジェクトを[Keys](../../../ado/reference/adox-api/keys-collection-adox.md)コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *キー*  
 追加する**キー**オブジェクト、または作成および追加するキーの名前。  
  
 *KeyType*  
 任意。 キーの種類を指定する**Long**型の値です。 *キー*パラメーターは、**キー**オブジェクトの[Type](../../../ado/reference/adox-api/type-property-key-adox.md)プロパティに対応します。  
  
 *列*  
 任意。 インデックスを作成する列の名前を指定する**文字列**値。 *Columns*パラメーターは、 [Column](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトの[Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティの値に対応しています。  
  
 *RelatedTable*  
 任意。 関連するテーブルの名前を示す**文字列**値です。 関連性*テーブル*のパラメーターは、 [Table](../../../ado/reference/adox-api/table-object-adox.md)オブジェクトの**Name**プロパティの値に対応しています。  
  
 *RelatedColumn*  
 任意。 外部キーに関連付けられている列の名前を示す**文字列**値です。 [関連性のある*列*のパラメーターは、 [Column](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトの**Name**プロパティの値に対応します。  
  
## <a name="remarks"></a>Remarks  
 *Columns*パラメーターには、列名または列名の配列のいずれかを指定できます。  
  
## <a name="applies-to"></a>適用対象  
 [Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append メソッド (ADOX Columns)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Indexes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX Procedures)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
