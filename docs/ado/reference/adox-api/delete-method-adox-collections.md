---
title: Delete メソッド (ADOX Collections) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be2aa91cf27d7dc12d3cd0c1e0bf719bd43797ab
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966435"
---
# <a name="delete-method-adox-collections"></a>Delete メソッド (ADOX Collections)
オブジェクトをコレクションから削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 削除するオブジェクトの名前または序数位置 (インデックス) を指定する**バリアント**です。  
  
## <a name="remarks"></a>Remarks  
 *名前*がコレクションに存在しない場合、エラーが発生します。  
  
 [テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)と[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)のコレクションでは、プロバイダーがテーブルまたはユーザーの削除をサポートしていない場合に、エラーが発生します。 [プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)および[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)コレクションでは、プロバイダーがコマンドの永続化をサポートしていない場合、 **Delete**は失敗します。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>参照  
 [Procedures Delete メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Views Delete メソッドの例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
