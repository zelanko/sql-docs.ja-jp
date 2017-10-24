---
title: "インデックスのオブジェクト (ADOX) |Microsoft ドキュメント"
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
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2fe0916836a44ecb61d1d606a9c894ac22342d57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="index-object-adox"></a>Index オブジェクト (ADOX)
データベース テーブルのインデックスを表します。  
  
## <a name="remarks"></a>解説  
 次のコードが新たに作成**インデックス**:  
  
```  
Dim obj As New Index  
```  
  
 プロパティのコレクションと、**インデックス**オブジェクトをすることができます。  
  
-   使用してインデックスを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   データベースを使用してインデックスの列へのアクセス、[列](../../../ado/reference/adox-api/columns-collection-adox.md)コレクション。  
  
-   インデックス キーがで一意である必要があるかどうかを指定して、 [Unique](../../../ado/reference/adox-api/unique-property-adox.md)プロパティです。  
  
-   インデックスを持つテーブルの主キーであるかどうかを指定して、 [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md)プロパティです。  
  
-   Null 値を持つインデックス フィールドにレコードがインデックス エントリを持つかどうかを指定、 [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md)プロパティです。  
  
-   インデックスがクラスター化するかどうかを指定して、 [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md)プロパティです。  
  
-   プロバイダーに固有のインデックスのプロパティへのアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
> [!NOTE]
>  追加するときにエラーが発生、[列](../../../ado/reference/adox-api/column-object-adox.md)を**列**のコレクション、**インデックス**場合、**列**に存在しません[テーブル](../../../ado/reference/adox-api/table-object-adox.md)オブジェクトに既に追加されて、[テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)コレクション。  
  
> [!NOTE]
>  データ プロバイダーはのすべてのプロパティをサポートしていません**インデックス**オブジェクト。 プロバイダーによってサポートされていないプロパティの値を設定した場合は、エラーが発生します。 新しい**インデックス**オブジェクト、オブジェクトはコレクションに追加するときにエラーが発生します。 既存のオブジェクトのプロパティを設定するときにエラーが発生します。  
  
> [!NOTE]
>  作成するときに**インデックス**オブジェクト、オプションのプロパティに適切な既定値が存在は、プロバイダーがプロパティをサポートしていることを保証されません。 詳細については、プロバイダーがサポートしているプロパティについて、プロバイダーのマニュアルを参照してください。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [インデックス オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [インデックスの追加メソッドの例 (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls プロパティの例 (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [主キーと一意のプロパティの例 (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [SortOrder プロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)

