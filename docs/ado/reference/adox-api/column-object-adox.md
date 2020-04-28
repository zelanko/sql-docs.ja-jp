---
title: Column オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db2c2dbe6af2a50fc2507a9ade92d83e0502f2ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966914"
---
# <a name="column-object-adox"></a>Column オブジェクト (ADOX)
テーブル、インデックス、またはキーからの列を表します。  
  
## <a name="remarks"></a>Remarks  
 次のコードでは、新しい**列**を作成します。  
  
 `Dim obj As New Column`  
  
 **Column**オブジェクトのプロパティとコレクションを使用すると、次のことができます。  
  
-   [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用して、列を特定します。  
  
-   [Type プロパティ (キー) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md)プロパティを使用して、列のデータ型を指定します。  
  
-   列が固定長であるかどうか、または[Attributes プロパティ (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md)プロパティを使用して null 値を含むことができるかどうかを確認します。  
  
-   列の最大サイズを指定するには、"設定された[サイズ" プロパティ (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md)プロパティを使用します。  
  
-   数値データ値の場合は、 [Numericscale プロパティ (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md)プロパティを使用して小数点以下桁数を指定します。  
  
-   数値データ値については、 [Precision プロパティ (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md)プロパティを使用して最大有効桁数を指定します。  
  
-   [ParentCatalog property (adox)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)プロパティを使用して、列を所有する[カタログオブジェクト (adox)](../../../ado/reference/adox-api/catalog-object-adox.md)を指定します。  
  
-   キー列の場合は、関連テーブル内の関連する列の名前を、"関連付け[列のプロパティ (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) " プロパティを使用して指定します。  
  
-   [インデックス列] では、並べ替え順序が並べ替え順序[として](../../../ado/reference/adox-api/sortorder-property-adox.md)昇順と降順のどちらであるかを指定します。  
  
-   [プロパティコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のプロパティにアクセスします。  
  
> [!NOTE]
>  **列**オブジェクトのすべてのプロパティがデータプロバイダーでサポートされているとは限りません。 プロバイダーがサポートしていないプロパティの値を設定した場合、エラーが発生します。 新しい**列**オブジェクトの場合、オブジェクトがコレクションに追加されるとエラーが発生します。 既存のオブジェクトの場合、プロパティの設定時にエラーが発生します。  
>   
>  **列**オブジェクトを作成するときに、オプションのプロパティに適切な既定値が存在しても、プロバイダーがプロパティをサポートしているかどうかは保証されません。 プロバイダーがサポートしているプロパティの詳細については、プロバイダーのドキュメントを参照してください。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Column オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close メソッド、Table Type プロパティの例 (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ADOX のコード例: NumericScale および Precision プロパティの例 (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [順序のプロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
