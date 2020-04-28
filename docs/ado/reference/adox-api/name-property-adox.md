---
title: Name プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 52808cf9e90c6779efb9f95e385f8df501bae870
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965767"
---
# <a name="name-property-adox"></a>Name プロパティ (ADOX)
オブジェクトの名前を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **文字列**値を設定または返します。  
  
## <a name="remarks"></a>Remarks  
 名前はコレクション内で一意である必要はありません。  
  
 **Name**プロパティは、[列](../../../ado/reference/adox-api/column-object-adox.md)、[グループ](../../../ado/reference/adox-api/group-object-adox.md)、[キー](../../../ado/reference/adox-api/key-object-adox.md)、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)、[テーブル](../../../ado/reference/adox-api/table-object-adox.md)、および[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトに対して読み取り/書き込みが可能です。 **Name**プロパティは、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)、[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)、および[ビュー](../../../ado/reference/adox-api/view-object-adox.md)オブジェクトでは読み取り専用です。  
  
 読み取り/書き込みオブジェクト (**列**、**グループ**、**キー**、**インデックス**、**テーブル**、**ユーザー**オブジェクト) の場合、既定値は空の文字列 ("") になります。  
  
> [!NOTE]
>  キーの場合、このプロパティは既にコレクションに追加されている**キー**オブジェクトに対して読み取り専用になります。 テーブルの場合、このプロパティは、既にコレクションに追加されている**テーブル**オブジェクトに対しては読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Index オブジェクト (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Key オブジェクト (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
