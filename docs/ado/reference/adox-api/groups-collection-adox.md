---
description: Groups コレクション (ADOX)
title: Groups コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5edecbbfebeea82d28f97bc31d15e04bf28c576a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770331"
---
# <a name="groups-collection-adox"></a>Groups コレクション (ADOX)
カタログまたはユーザーの格納されているすべての [グループ](./group-object-adox.md) オブジェクトが含まれます。  
  
## <a name="remarks"></a>解説  
 [カタログ](./catalog-object-adox.md)の**Groups**コレクションは、すべてのカタログのグループアカウントを表します。 [ユーザー](./user-object-adox.md)の**Groups**コレクションは、ユーザーが属しているグループのみを表します。  
  
 **Groups**コレクションの[Append](./append-method-adox-groups.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **追加**メソッドを使用して、新しいセキュリティグループをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [項目](../ado-api/item-property-ado.md)プロパティを使用して、コレクション内のグループにアクセスします。  
  
-   [Count](../ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれるグループの数を返します。  
  
-   [Delete](./delete-method-adox-collections.md)メソッドを使用して、コレクションからグループを削除します。  
  
-   [更新](../ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
> [!NOTE]
>  **グループ**オブジェクトを**ユーザー**オブジェクトの**groups**コレクションに追加する前に、追加するオブジェクトと同じ[名前](./name-property-adox.md)の**グループ**オブジェクトが、**カタログ**の**groups**コレクションに既に存在している必要があります。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Groups コレクションのプロパティ、メソッド、およびイベント](./groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Catalog オブジェクト (ADOX)](./catalog-object-adox.md)   
 [Group オブジェクト (ADOX)](./group-object-adox.md)