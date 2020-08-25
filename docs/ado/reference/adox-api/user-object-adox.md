---
description: User オブジェクト (ADOX)
title: User オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3576c64d620956b69dbd33113a3d114ff55b4a79
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769102"
---
# <a name="user-object-adox"></a>User オブジェクト (ADOX)
セキュリティで保護されたデータベース内でアクセス許可を持つユーザーアカウントを表します。  
  
## <a name="remarks"></a>解説  
 [カタログ](./catalog-object-adox.md)の[ユーザー](./users-collection-adox.md)コレクションは、すべてのカタログのユーザーを表します。 [グループ](./group-object-adox.md)の**ユーザー**コレクションは、特定のグループのユーザーのみを表します。  
  
 **ユーザー**オブジェクトのプロパティ、コレクション、およびメソッドを使用すると、次のことができます。  
  
-   [Name](./name-property-adox.md)プロパティを使用してユーザーを識別します。  
  
-   [ChangePassword](./changepassword-method-adox.md)メソッドを使用して、ユーザーのパスワードを変更します。  
  
-   ユーザーが [getpermissions](./getpermissions-method-adox.md) メソッドと [SetPermissions](./setpermissions-method-adox.md) メソッドを使用して、読み取り、書き込み、または削除のアクセス許可を持っているかどうかを確認します。  
  
-   [グループ](./groups-collection-adox.md)コレクションに属しているユーザーが属するグループにアクセスします。  
  
-   [プロパティ](../ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のプロパティにアクセスします。  
  
-   ユーザーの [ParentCatalog](./parentcatalog-property-adox.md) を決定します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [User オブジェクトのプロパティ、メソッド、およびイベント](./user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [GetPermissions および SetPermissions メソッドの例 (VB)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups コレクション (ADOX)](./groups-collection-adox.md)   
 [Users コレクション (ADOX)](./users-collection-adox.md)