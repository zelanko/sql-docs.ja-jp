---
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
ms.openlocfilehash: e2b6e7b7669e0976cf47e5b4d5d2c827a824f919
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764853"
---
# <a name="groups-collection-adox"></a>Groups コレクション (ADOX)
カタログまたはユーザーの格納されているすべての[グループ](../../../ado/reference/adox-api/group-object-adox.md)オブジェクトが含まれます。  
  
## <a name="remarks"></a>Remarks  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)の**Groups**コレクションは、すべてのカタログのグループアカウントを表します。 [ユーザー](../../../ado/reference/adox-api/user-object-adox.md)の**Groups**コレクションは、ユーザーが属しているグループのみを表します。  
  
 **Groups**コレクションの[Append](../../../ado/reference/adox-api/append-method-adox-groups.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **追加**メソッドを使用して、新しいセキュリティグループをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して、コレクション内のグループにアクセスします。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれるグループの数を返します。  
  
-   [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用して、コレクションからグループを削除します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
> [!NOTE]
>  **グループ**オブジェクトを**ユーザー**オブジェクトの**groups**コレクションに追加する前に、追加するオブジェクトと同じ[名前](../../../ado/reference/adox-api/name-property-adox.md)の**グループ**オブジェクトが、**カタログ**の**groups**コレクションに既に存在している必要があります。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Groups コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
