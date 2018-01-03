---
title: "テーブルのオブジェクト (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Table
helpviewer_keywords: Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd6d351f97d2b6357b8d4156c3208fb4f32a4805
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="table-object-adox"></a>Table オブジェクト (ADOX)
列、インデックス、およびキーを含むデータベース テーブルを表します。  
  
## <a name="remarks"></a>解説  
 次のコードが新たに作成**テーブル**:  
  
```  
Dim obj As New Table  
```  
  
 プロパティのコレクションと、**テーブル**オブジェクトをすることができます。  
  
-   テーブルを識別、[名プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   テーブルの種類を判断、 [Type プロパティ (テーブル) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)プロパティです。  
  
-   データベースを含むテーブルの列へのアクセス、[列コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)コレクション。  
  
-   テーブルのインデックスにアクセス、[インデックス コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)です。  
  
-   アクセスを持つテーブルのキー、[キー コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)です。  
  
-   テーブルを所有するカタログを指定して、 [ParentCatalog プロパティ (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)プロパティです。  
  
-   日付情報を返す、 [DateCreated プロパティ (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)と[DateModified プロパティ (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティです。  
  
-   プロバイダーに固有のテーブルのプロパティへのアクセス、[プロパティ コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
> [!NOTE]
>  データ プロバイダーはのすべてのプロパティをサポートしていません**テーブル**オブジェクト。 プロバイダーがサポートしていないプロパティの値を設定した場合は、エラーが発生します。 新しい**テーブル**オブジェクト、オブジェクトはコレクションに追加するときにエラーが発生します。 既存のオブジェクトのプロパティを設定するときにエラーが発生します。  
>   
>  作成するときに**テーブル**オブジェクト、オプションのプロパティに適切な既定値が存在は、プロバイダーがプロパティをサポートしていることを保証されません。 詳細については、プロバイダーがサポートしているプロパティについて、プロバイダーのマニュアルを参照してください。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Table オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [カタログ ActiveConnection プロパティの例 (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [列とテーブル名プロパティの例 (VB) のメソッドを追加します。](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [テーブル型のプロパティの例 (VB) である接続 Close メソッド](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [キーのコレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
