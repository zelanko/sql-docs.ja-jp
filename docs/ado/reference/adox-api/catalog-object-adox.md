---
title: Catalog オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9843ad9ac0a456f7e38e741e08ce9b66f862fd9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967055"
---
# <a name="catalog-object-adox"></a>Catalog オブジェクト (ADOX)
データソースのスキーマカタログを記述するコレクション ([テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)、[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)、[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)、[グループ](../../../ado/reference/adox-api/groups-collection-adox.md)、および[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)) が格納されます。  
  
## <a name="remarks"></a>Remarks  
 **カタログ**オブジェクトを変更するには、オブジェクトを追加または削除するか、既存のオブジェクトを変更します。 一部のプロバイダーでは、すべての**カタログ**オブジェクトがサポートされていない場合や、スキーマ情報の表示のみがサポートされている場合があります。  
  
 **Catalog**オブジェクトのプロパティとメソッドを使用すると、次のことができます。  
  
-   [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)プロパティを ADO [connection](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトまたは有効な接続文字列に設定して、カタログを開きます。  
  
-   [Create](../../../ado/reference/adox-api/create-method-adox.md)メソッドを使用して、新しいカタログを作成します。  
  
-   [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md)メソッドと[SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)メソッドを使用して、**カタログ**内のオブジェクトの所有者を特定します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Catalog オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Catalog ActiveConnection プロパティの例 (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Command プロパティと CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Connection Close メソッド、Table Type プロパティの例 (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Create メソッドの例 (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Parameters コレクション、Command プロパティの例 (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedures Append メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedures Delete メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures Refresh メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Views および Fields コレクションの例 (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views Append メソッドの例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views Collection、CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views Delete メソッドの例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views Refresh メソッドの例 (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
