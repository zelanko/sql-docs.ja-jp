---
description: ChangePassword メソッド (ADOX)
title: ChangePassword メソッド (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
author: rothja
ms.author: jroth
ms.openlocfilehash: d23920fff14bfa04020223ad0150f480f6073723
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440374"
---
# <a name="changepassword-method-adox"></a>ChangePassword メソッド (ADOX)
[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)アカウントのパスワードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>パラメーター  
 *OldPassword*  
 ユーザーの既存のパスワードを示す **文字列** 値です。 ユーザーが現在パスワードを持っていない場合は、 *Oldpassword*に空の文字列 ("") を使用します。  
  
 *NewPassword*  
 新しいパスワードを示す **文字列** 値です。  
  
## <a name="remarks"></a>解説  
 セキュリティ上の理由から、新しいパスワードに加えて古いパスワードも指定する必要があります。  
  
 プロバイダーがトラスティのプロパティの管理をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Groups および Users Append、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
