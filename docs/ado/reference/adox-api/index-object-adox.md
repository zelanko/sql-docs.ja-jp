---
title: Index オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
author: rothja
ms.author: jroth
ms.openlocfilehash: 840484cbfcb1feeb56022835b6c1b3157101edb8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763883"
---
# <a name="index-object-adox"></a>Index オブジェクト (ADOX)
データベーステーブルのインデックスを表します。  
  
## <a name="remarks"></a>Remarks  
 次のコードでは、新しい**インデックス**を作成します。  
  
```  
Dim obj As New Index  
```  
  
 **インデックス**オブジェクトのプロパティとコレクションを使用すると、次のことができます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してインデックスを識別します。  
  
-   [Columns](../../../ado/reference/adox-api/columns-collection-adox.md)コレクションを使用して、インデックスのデータベース列にアクセスします。  
  
-   インデックスキーが[一意](../../../ado/reference/adox-api/unique-property-adox.md)のプロパティで一意である必要があるかどうかを指定します。  
  
-   インデックスが[PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md)プロパティを持つテーブルの主キーであるかどうかを指定します。  
  
-   インデックスフィールドに null 値を持つレコードのインデックスエントリが[IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md)プロパティに設定されているかどうかを指定します。  
  
-   [クラスター](../../../ado/reference/adox-api/clustered-property-adox.md)化されたプロパティを使用してインデックスをクラスター化するかどうかを指定します。  
  
-   [プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のインデックスプロパティにアクセスします。  
  
> [!NOTE]
>  [テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)コレクションに既に追加されている[テーブル](../../../ado/reference/adox-api/table-object-adox.md)オブジェクト**に列が**存在しない場合、**インデックス**の**Columns**コレクションに[列](../../../ado/reference/adox-api/column-object-adox.md)を追加すると、エラーが発生します。  
  
> [!NOTE]
>  データプロバイダーが、**インデックス**オブジェクトのすべてのプロパティをサポートしていない可能性があります。 プロバイダーでサポートされていないプロパティの値を設定した場合は、エラーが発生します。 新しい**インデックス**オブジェクトの場合、オブジェクトがコレクションに追加されるとエラーが発生します。 既存のオブジェクトの場合、プロパティの設定時にエラーが発生します。  
  
> [!NOTE]
>  **インデックス**オブジェクトを作成するときに、オプションのプロパティに適切な既定値が存在しても、プロバイダーがプロパティをサポートしているかどうかは保証されません。 プロバイダーがサポートしているプロパティの詳細については、プロバイダーのドキュメントを参照してください。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Index オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Indexes Append メソッドの例 (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls プロパティの例 (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey および Unique プロパティの例 (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [順序のプロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
