---
title: Group オブジェクト (ADOX) |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b0cd75780abe01edc6f2e90258cc7d24f5eae016
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763323"
---
# <a name="group-object-adox"></a>Group オブジェクト (ADOX)
セキュリティで保護されたデータベース内でアクセス許可を持つグループアカウントを表します。  
  
## <a name="remarks"></a>解説  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)の[Groups](../../../ado/reference/adox-api/groups-collection-adox.md)コレクションは、すべてのカタログのグループアカウントを表します。 [ユーザー](../../../ado/reference/adox-api/user-object-adox.md)の**Groups**コレクションは、ユーザーが属しているグループのみを表します。  
  
 **Group**オブジェクトのプロパティ、コレクション、およびメソッドを使用すると、次のことができます。  
  
-   "[名前](../../../ado/reference/adox-api/name-property-adox.md)" プロパティを使用してグループを識別します。  
  
-   グループに、 [getpermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)および[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)メソッドを使用した読み取り、書き込み、または削除のアクセス許可があるかどうかを確認します。  
  
-   [ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクションを使用して、グループ内のメンバーシップを持つユーザーアカウントにアクセスします。  
  
-   [プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のプロパティにアクセスします。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Group オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
