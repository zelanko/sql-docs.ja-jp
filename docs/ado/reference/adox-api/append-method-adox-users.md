---
title: Append メソッド (ADOX Users) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4c1f772b041aa5f7be2c1fc0c7aeb7c69189b5d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708333"
---
# <a name="append-method-adox-users"></a>Append メソッド (ADOX Users)
新しく追加[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトを[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ユーザー*  
 A**バリアント**値を含む、**ユーザー**オブジェクトを追加するか、ユーザーを作成し、追加の名前。  
  
 *Password*  
 任意。 A**文字列**ユーザーのパスワードを表す値です。 *パスワード*パラメーターによって指定された値に対応、 [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)のメソッド、**ユーザー**オブジェクト。  
  
## <a name="remarks"></a>コメント  
 **ユーザー**のコレクションを[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)カタログのすべてのユーザーを表します。 **ユーザー**のコレクションを[グループ](../../../ado/reference/adox-api/group-object-adox.md)を特定のグループのメンバーシップを持つユーザーのみを表します。  
  
 プロバイダーがユーザーの作成をサポートしていない場合、エラーが発生します。  
  
> [!NOTE]
>  追加の前に、**ユーザー**オブジェクトを**ユーザー**のコレクションを**グループ**オブジェクト、**ユーザー**オブジェクトと同じ[名](../../../ado/reference/adox-api/name-property-adox.md)ように追加する 1 つに既に存在する必要があります、**ユーザー**のコレクション、**カタログ**します。  
  
## <a name="applies-to"></a>適用対象  
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Groups および Users Append、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append メソッド (ADOX Columns)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Indexes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX Keys)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX Procedures)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
