---
title: "Append メソッド (ADOX グループ) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Groups::raw_Append
- Groups::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 232f7d51b00d9c22689f126518bbaddacc9a3b8f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="append-method-adox-groups"></a>Append メソッド (ADOX グループ)
新しく追加[グループ](../../../ado/reference/adox-api/group-object-adox.md)オブジェクトを[グループ](../../../ado/reference/adox-api/groups-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>パラメーター  
 *[グループ]*  
 **グループ**追加するオブジェクトまたはグループを作成し、追加の名前。  
  
## <a name="remarks"></a>解説  
 **グループ**のコレクション、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)のすべてのカタログのグループ アカウントを表します。 **グループ**のコレクション、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)ユーザーが所属するグループのみを表します。  
  
 プロバイダーがグループの作成をサポートしていない場合は、エラーが発生します。  
  
> [!NOTE]
>  追加の前に、**グループ**オブジェクトを**グループ**のコレクション、**ユーザー**オブジェクト、**グループ**が同じオブジェクト[名前](../../../ado/reference/adox-api/name-property-adox.md)追加する 1 つに既に存在すると、**グループ**のコレクション、**カタログ**です。  
  
## <a name="applies-to"></a>適用対象  
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [グループとユーザーの追加、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append メソッド (ADOX 列)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX インデックス)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX キー)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX プロシージャ)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX ユーザー)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
