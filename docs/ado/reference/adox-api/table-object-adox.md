---
title: Table オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
author: rothja
ms.author: jroth
ms.openlocfilehash: bcebe14b7b989e584539dd3f92fd8ea676ebd48a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763303"
---
# <a name="table-object-adox"></a>Table オブジェクト (ADOX)
列、インデックス、およびキーを含むデータベーステーブルを表します。  
  
## <a name="remarks"></a>解説  
 次のコードでは、新しい**テーブル**を作成します。  
  
```  
Dim obj As New Table  
```  
  
 **Table**オブジェクトのプロパティとコレクションを使用すると、次のことができます。  
  
-   [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してテーブルを識別します。  
  
-   [Type プロパティ (table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)プロパティを使用して、テーブルの種類を決定します。  
  
-   [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)コレクションを使用して、テーブルのデータベース列にアクセスします。  
  
-   [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)を使用してテーブルのインデックスにアクセスします。  
  
-   [キーコレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)を使用してテーブルのキーにアクセスします。  
  
-   [ParentCatalog プロパティ (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)プロパティを使用して、テーブルを所有するカタログを指定します。  
  
-   [DateCreated プロパティ (adox)](../../../ado/reference/adox-api/datecreated-property-adox.md)と[DATEMODIFIED property (adox)](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティを使用して日付情報を返します。  
  
-   [プロパティコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のテーブルプロパティにアクセスします。  
  
> [!NOTE]
>  データプロバイダーが**テーブル**オブジェクトのすべてのプロパティをサポートしていない可能性があります。 プロバイダーがサポートしていないプロパティの値を設定した場合、エラーが発生します。 新しい**テーブル**オブジェクトの場合、オブジェクトがコレクションに追加されるとエラーが発生します。 既存のオブジェクトの場合、プロパティの設定時にエラーが発生します。  
>   
>  **テーブル**オブジェクトを作成するときに、オプションのプロパティに適切な既定値が存在しても、プロバイダーがプロパティをサポートしているかどうかは保証されません。 プロバイダーがサポートしているプロパティの詳細については、プロバイダーのドキュメントを参照してください。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Table オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Catalog ActiveConnection プロパティの例 (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close メソッド、Table Type プロパティの例 (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
