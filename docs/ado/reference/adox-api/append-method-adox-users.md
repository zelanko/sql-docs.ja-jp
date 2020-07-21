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
author: rothja
ms.author: jroth
ms.openlocfilehash: c010b291468432544a037d15fbaa790fc3ee789d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764023"
---
# <a name="append-method-adox-users"></a>Append メソッド (ADOX Users)
新しい[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトを[Users](../../../ado/reference/adox-api/users-collection-adox.md)コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ユーザー*  
 追加する**ユーザー**オブジェクトまたは作成して追加するユーザーの名前を含む**バリアント**値。  
  
 *パスワード*  
 省略可能。 ユーザーのパスワードを含む**文字列**値です。 *Password*パラメーターは、**ユーザー**オブジェクトの[ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)メソッドによって指定された値に対応します。  
  
## <a name="remarks"></a>Remarks  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)の**ユーザー**コレクションは、すべてのカタログのユーザーを表します。 [グループ](../../../ado/reference/adox-api/group-object-adox.md)の**ユーザー**コレクションは、特定のグループのメンバーシップを持つユーザーのみを表します。  
  
 プロバイダーがユーザーの作成をサポートしていない場合、エラーが発生します。  
  
> [!NOTE]
>  **ユーザー**オブジェクトを**グループ**オブジェクトの**users**コレクションに追加する前に、追加する**ユーザーオブジェクトが****カタログ**の**users**コレクションに既に存在[している](../../../ado/reference/adox-api/name-property-adox.md)必要があります。  
  
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
