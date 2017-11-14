---
title: "テーブルのコレクション (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1489bb1716cb29116e385158e6f05dcc3d028431
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="tables-collection-adox"></a>テーブル コレクション (ADOX)
すべてを含む[テーブル](../../../ado/reference/adox-api/table-object-adox.md)カタログのオブジェクト。  
  
## <a name="remarks"></a>解説  
 [Append](../../../ado/reference/adox-api/append-method-adox-tables.md)のメソッド、**テーブル**コレクションは ADOX に一意です。 可能な代替手段としては以下の方法があります。  
  
-   使用して、コレクションに新しいテーブルを追加、 **Append**メソッドです。  
  
 残りのプロパティとメソッドは、standard ADO コレクションには、 可能な代替手段としては以下の方法があります。  
  
-   コレクション内にテーブルへのアクセス、[項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティです。  
  
-   コレクション内に含まれているテーブルの数を返す、[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティです。  
  
-   テーブルを使用して、コレクションから削除、[削除](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドです。  
  
-   現在のデータベース スキーマを反映するようにコレクション内のオブジェクトを更新、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドです。  
  
 一部のプロバイダーで、ビューなどの他のスキーマ オブジェクトを返す可能性があります、**テーブル**コレクション。 そのため、ADOX コレクションの中には、同じオブジェクトに複数の参照があります。 1 つのコレクションからオブジェクトを削除する必要があります、変更は表示されませんまで削除されたオブジェクトを参照する別のコレクションで、**更新**メソッドは、コレクションに対して呼び出されます。 たとえばで、OLE DB Provider for Jet、ビューが返されますと、**テーブル**コレクション。 更新する必要があるビューを削除する場合、**テーブル**コレクション、コレクション変更が反映される前にします。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [テーブル コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [カタログ ActiveConnection プロパティの例 (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [列とテーブル名プロパティの例 (VB) のメソッドを追加します。](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [テーブル型のプロパティの例 (VB) である接続 Close メソッド](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)

