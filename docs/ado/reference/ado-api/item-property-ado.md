---
title: "Item プロパティ (ADO) |Microsoft ドキュメント"
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
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 59779714027c0ff619293d01de851daec7bbe158
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="item-property-ado"></a>Item プロパティ (ADO)
名前または序数で、コレクションの特定のメンバーを示します。  
  
## <a name="syntax"></a>構文  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>戻り値  
 オブジェクト参照を返します。  
  
## <a name="parameters"></a>パラメーター  
 *インデックス*  
 A**バリアント**名前またはコレクション内のオブジェクトの序数のいずれかに評価される式。  
  
## <a name="remarks"></a>解説  
 使用して、**項目**プロパティをコレクションから特定のオブジェクトを取得します。 場合**項目**に対応するコレクションでオブジェクトを検索することはできません、*インデックス*引数、エラーが発生します。 また、一部のコレクションが名前付きオブジェクトをサポートしません。これらのコレクションの序数参照を使用する必要があります。  
  
 **項目**プロパティは、すべてのコレクションの既定のプロパティです。 したがって、次の構文形式を相互交換。  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[グループのコレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[キーのコレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[メンバーのコレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[位置コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[プロシージャのコレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[テーブル コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[ユーザー コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[ビューのコレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [項目プロパティの例 (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [項目プロパティの例 (vc++)](../../../ado/reference/ado-api/item-property-example-vc.md)   

