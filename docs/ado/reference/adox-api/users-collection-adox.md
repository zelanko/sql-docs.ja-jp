---
title: Users コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 4befb68c861edee0f5c1423e86ee1fb21067c2a5
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753179"
---
# <a name="users-collection-adox"></a>Users コレクション (ADOX)
[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)の格納されているすべての[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトが含まれます。  
  
## <a name="remarks"></a>解説  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)の**ユーザー**コレクションは、すべてのカタログのユーザーを表します。 [グループ](../../../ado/reference/adox-api/group-object-adox.md)の**ユーザー**コレクションは、特定のグループのメンバーシップを持つユーザーのみを表します。  
  
 **ユーザー**コレクションの[Append](../../../ado/reference/adox-api/append-method-adox-users.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **Append**メソッドを使用して、新しいユーザーをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して、コレクション内のユーザーにアクセスします。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクションに格納されているユーザーの数を返します。  
  
-   [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用して、コレクションからユーザーを削除します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベースのスキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
> [!NOTE]
>  **ユーザー**オブジェクトを**グループ**オブジェクトの**users**コレクションに追加する前に、追加する**ユーザーオブジェクトが****カタログ**の**users**コレクションに既に存在[している](../../../ado/reference/adox-api/name-property-adox.md)必要があります。  
  
 ここでは、次のトピックについて説明します。  
  
-   [User コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [GetPermissions および SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
