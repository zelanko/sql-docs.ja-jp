---
title: ChangePassword メソッド (ADOX) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 111f549f419404b8174d90e3d1298a7c3789913d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="changepassword-method-adox"></a>ChangePassword メソッド (ADOX)
パスワードを変更、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)アカウント。  
  
## <a name="syntax"></a>構文  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>パラメーター  
 *OldPassword*  
 A**文字列**ユーザーの既存のパスワードを指定する値。 ユーザーがパスワードを持っていない現在場合は、空の文字列を使用して ("") の*OldPassword*です。  
  
 *NewPassword*  
 A**文字列**新しいパスワードを指定する値。  
  
## <a name="remarks"></a>解説  
 セキュリティ上の理由には、新しいパスワードに加え、古いパスワードを指定してください。  
  
 プロバイダーが trustee プロパティの管理をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Groups および Users Append、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
