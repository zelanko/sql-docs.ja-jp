---
title: ユーザー コレクション (ADOX) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7a075a12efcf401a5ba2458a90f410b3eb2586b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287231"
---
# <a name="users-collection-adox"></a>ユーザー コレクション (ADOX)
すべてを含むストアド[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)のオブジェクト、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)です。  
  
## <a name="remarks"></a>コメント  
 **ユーザー**のコレクション、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)カタログのすべてのユーザーを表します。 **ユーザー**のコレクション、[グループ](../../../ado/reference/adox-api/group-object-adox.md)特定のグループ メンバーシップを持つユーザーのみを表します。  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-users.md)のメソッド、**ユーザー**コレクションは ADOX に一意です。 可能な代替手段としては以下の方法があります。  
  
-   使用してコレクションに新しいユーザーを追加、 **Append**メソッドです。  
  
 残りのプロパティとメソッドは、standard ADO コレクションには、 可能な代替手段としては以下の方法があります。  
  
-   使用して、コレクション内のユーザーのアクセス、[項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティです。  
  
-   使用して、コレクションに含まれるユーザーの数を返す、[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティです。  
  
-   使用して、コレクションからユーザーを削除、[削除](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドです。  
  
-   現在のデータベースのスキーマを反映するようにコレクション内のオブジェクトを更新、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドです。  
  
> [!NOTE]
>  追加の前に、**ユーザー**オブジェクトを**ユーザー**のコレクション、**グループ**オブジェクト、**ユーザー**が同じオブジェクト[名](../../../ado/reference/adox-api/name-property-adox.md)追加する 1 つに既に存在すると、**ユーザー**のコレクション、**カタログ**です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [User コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [GetPermissions と SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
