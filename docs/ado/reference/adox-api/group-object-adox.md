---
title: "グループ オブジェクト (ADOX) |Microsoft ドキュメント"
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
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16aad2cd94a457d3d6efe97326fdbe7e6c06e53d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="group-object-adox"></a>グループ オブジェクト (ADOX)
セキュリティで保護されたデータベース内でのアクセス許可を持つグループ アカウントを表します。  
  
## <a name="remarks"></a>解説  
 [グループ](../../../ado/reference/adox-api/groups-collection-adox.md)のコレクション、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)カタログのすべてのグループ アカウントを表します。 **グループ**のコレクション、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)ユーザーが所属するグループのみを表します。  
  
 プロパティ、コレクション、方法と、**グループ**オブジェクトをすることができます。  
  
-   グループを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   グループが読み取りになっているかどうかを判断書き込み、またはを使用した権限の削除、 [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)と[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)メソッドです。  
  
-   グループのメンバーシップを持っているユーザー アカウントにアクセス、[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクション。  
  
-   プロバイダーに固有のプロパティへのアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [オブジェクトのプロパティ、メソッド、およびイベントをグループ化します。](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [グループのコレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [ユーザー コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
