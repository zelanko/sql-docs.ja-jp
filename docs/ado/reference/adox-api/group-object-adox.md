---
title: グループ オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 537e0d3b1408a3cb159a79ad4e256fc8b5cf720f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635190"
---
# <a name="group-object-adox"></a>Group オブジェクト (ADOX)
セキュリティで保護されたデータベース内のアクセス許可を持つグループ アカウントを表します。  
  
## <a name="remarks"></a>コメント  
 [グループ](../../../ado/reference/adox-api/groups-collection-adox.md)のコレクションを[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)カタログのすべてのグループ アカウントを表します。 **グループ**のコレクションを[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)ユーザーが所属するグループのみを表します。  
  
 プロパティ、コレクション、およびメソッドの使用、**グループ**オブジェクトのことができます。  
  
-   グループを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティ。  
  
-   グループが読み取りになっているかどうかを判断する書き込み、または削除のアクセス許可、 [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)と[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)メソッド。  
  
-   持つグループのメンバーシップを持っているユーザー アカウントにアクセス、[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクション。  
  
-   プロバイダー固有のプロパティにアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Group オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
