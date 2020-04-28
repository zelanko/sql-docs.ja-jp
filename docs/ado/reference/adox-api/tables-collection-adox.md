---
title: Tables コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0bf28af10084a30a5c81c76fe7e44781178979ad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965130"
---
# <a name="tables-collection-adox"></a>Tables コレクション (ADOX)
カタログのすべての[テーブル](../../../ado/reference/adox-api/table-object-adox.md)オブジェクトが含まれます。  
  
## <a name="remarks"></a>Remarks  
 **Tables**コレクションの[Append](../../../ado/reference/adox-api/append-method-adox-tables.md)メソッドは、ADOX で一意です。 次の操作を行うことができます。  
  
-   **追加**メソッドを使用して、新しいテーブルをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次の操作を行うことができます。  
  
-   [Item](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して、コレクション内のテーブルにアクセスします。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれるテーブルの数を返します。  
  
-   [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用して、テーブルをコレクションから削除します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
 プロバイダーによっては、 **Tables**コレクション内の他のスキーマオブジェクト (ビューなど) が返される場合があります。 そのため、一部の ADOX コレクションには、同じオブジェクトへの複数の参照を含めることができます。 オブジェクトを1つのコレクションから削除すると、その変更は、コレクションで**Refresh**メソッドが呼び出されるまで、削除されたオブジェクトを参照する別のコレクションに表示されません。 たとえば、Microsoft Jet の OLE DB Provider を使用すると、 **Tables**コレクションと共にビューが返されます。 ビューを削除する場合は、コレクションに変更が反映される前に、 **Tables**コレクションを更新する必要があります。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Tables コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Catalog ActiveConnection プロパティの例 (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close メソッド、Table Type プロパティの例 (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
