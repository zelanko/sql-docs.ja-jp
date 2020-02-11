---
title: Item プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6fe7e807fc38d6f1cf6f72e5b19539bb839e9c08
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918360"
---
# <a name="item-property-ado"></a>Item プロパティ (ADO)
名前または序数を指定して、コレクションの特定のメンバーを示します。  
  
## <a name="syntax"></a>構文  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>戻り値  
 オブジェクト参照を返します。  
  
## <a name="parameters"></a>パラメーター  
 *化*  
 コレクション内のオブジェクトの名前または序数に評価される**バリアント**式。  
  
## <a name="remarks"></a>解説  
 コレクション内の特定のオブジェクトを返すには、 **Item**プロパティを使用します。 **Item**が*Index*引数に対応するコレクション内のオブジェクトを見つけられない場合、エラーが発生します。 また、一部のコレクションでは名前付きオブジェクトがサポートされていません。これらのコレクションでは、序数参照を使用する必要があります。  
  
 **Item**プロパティは、すべてのコレクションの既定のプロパティです。したがって、次の構文形式は置き換えることができます。  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [Item プロパティの例 (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Item プロパティの例 (VC++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
