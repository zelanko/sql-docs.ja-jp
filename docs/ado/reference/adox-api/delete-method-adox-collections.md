---
title: "Delete メソッド (ADOX コレクション) |Microsoft ドキュメント"
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
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72dd3f6d514b20bb28f9daee6fc16c5c7c346095
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-adox-collections"></a>Delete メソッド (ADOX コレクション)
コレクションからオブジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 A**バリアント**名前または削除するオブジェクトの位置 (インデックス) を表す序数を指定します。  
  
## <a name="remarks"></a>解説  
 場合、エラーが発生、*名前*コレクションに存在しません。  
  
 [テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)と[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクション、エラーが発生、プロバイダーがサポートしない場合のテーブルやユーザーの削除それぞれします。 [プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)と[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)コレクション、**削除**プロバイダーは永続的なコマンドをサポートしていない場合は失敗します。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[グループのコレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[キーのコレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[プロシージャのコレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[テーブル コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[ユーザー コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[ビューのコレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>参照  
 [プロシージャの削除の方法の例 (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [ビューの削除の方法の例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
