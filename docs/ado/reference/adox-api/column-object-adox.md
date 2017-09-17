---
title: "Column オブジェクト (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5a8a5047f4cd4655ebe1dd041e44949ca361c54
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="column-object-adox"></a>Column オブジェクト (ADOX)
テーブル、インデックス、またはキーから列を表します。  
  
## <a name="remarks"></a>解説  
 次のコードが新たに作成**列**:  
  
 `Dim obj As New Column`  
  
 プロパティのコレクションと、**列**オブジェクトをすることができます。  
  
-   列を識別、[名プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   列のデータ型の指定、 [Type プロパティ (キー) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md)プロパティです。  
  
-   決定列が固定長の場合、または null 値を含めることができます、[属性プロパティ (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md)プロパティです。  
  
-   列の最大サイズを指定する、 [DefinedSize プロパティ (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md)プロパティです。  
  
-   数値データの値で小数点以下桁数を指定する、 [NumericScale プロパティ (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md)プロパティです。  
  
-   数値データ値と最大有効桁数を指定する、[精度プロパティ (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md)プロパティです。  
  
-   指定して、[カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)を持つ列を所有している、 [ParentCatalog プロパティ (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)プロパティです。  
  
-   キー列の場合、関連テーブルで関連する列の名前を指定します、 [RelatedColumn プロパティ (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md)プロパティです。  
  
-   インデックス列を指定するかどうか、並べ替え順序が昇順または降順で、 [SortOrder プロパティ (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md)プロパティです。  
  
-   プロバイダーに固有のプロパティへのアクセス、[プロパティ コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
> [!NOTE]
>  すべてのプロパティの**列**オブジェクトは、データ プロバイダーでサポートすることがあります。 プロバイダーがサポートしていないプロパティの値を設定した場合は、エラーが発生します。 新しい**列**オブジェクト、オブジェクトはコレクションに追加するときにエラーが発生します。 既存のオブジェクトのプロパティを設定するときにエラーが発生します。  
>   
>  作成するときに**列**オブジェクト、オプションのプロパティに適切な既定値が存在は、プロバイダーがプロパティをサポートしていることを保証されません。 詳細については、プロバイダーがサポートしているプロパティについて、プロバイダーのマニュアルを参照してください。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [列オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [列とテーブル名プロパティの例 (VB) のメソッドを追加します。](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [テーブル型のプロパティの例 (VB) である接続 Close メソッド](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ADOX コードの例: NumericScale し (VB) の有効桁数のプロパティの例](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [SortOrder プロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
