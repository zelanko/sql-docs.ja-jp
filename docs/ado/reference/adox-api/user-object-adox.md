---
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
ms.openlocfilehash: 55315ab64f87c6aba1c988c752c4e21811fef35c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762713"
---
# <a name="user-object-adox"></a>User オブジェクト (ADOX)
セキュリティで保護されたデータベース内でアクセス許可を持つユーザーアカウントを表します。  
  
## <a name="remarks"></a>解説  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)の[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)コレクションは、すべてのカタログのユーザーを表します。 [グループ](../../../ado/reference/adox-api/group-object-adox.md)の**ユーザー**コレクションは、特定のグループのユーザーのみを表します。  
  
 **ユーザー**オブジェクトのプロパティ、コレクション、およびメソッドを使用すると、次のことができます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してユーザーを識別します。  
  
-   [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)メソッドを使用して、ユーザーのパスワードを変更します。  
  
-   ユーザーが[getpermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)メソッドと[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)メソッドを使用して、読み取り、書き込み、または削除のアクセス許可を持っているかどうかを確認します。  
  
-   [グループ](../../../ado/reference/adox-api/groups-collection-adox.md)コレクションに属しているユーザーが属するグループにアクセスします。  
  
-   [プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有のプロパティにアクセスします。  
  
-   ユーザーの[ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md)を決定します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [User オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [GetPermissions および SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
