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
ms.openlocfilehash: 99a21cd5dd32af9e84877865cfe7c0fc92f6c087
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967224"
---
# <a name="append-method-adox-users"></a>Append メソッド (ADOX Users)
新しい[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトを[Users](../../../ado/reference/adox-api/users-collection-adox.md)コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *User*  
 追加する**ユーザー**オブジェクトまたは作成して追加するユーザーの名前を含む**バリアント**値。  
  
 *パスワード*  
 省略可能。 ユーザーのパスワードを含む**文字列**値です。 *Password*パラメーターは、**ユーザー**オブジェクトの[ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)メソッドによって指定された値に対応します。  
  
## <a name="remarks"></a>解説  
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
