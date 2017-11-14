---
title: "ChangePassword メソッド (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 18dd53bc701cf6a4b77c8e77f5b1851aff57f2ba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="changepassword-method-adox"></a>ChangePassword メソッド (ADOX)
パスワードを変更、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)アカウント。  
  
## <a name="syntax"></a>構文  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Oldpassword \*  
 A**文字列**ユーザーの既存のパスワードを指定する値。 ユーザーがパスワードを持っていない現在場合は、空の文字列を使用して ("") の*OldPassword*です。  
  
 *新しいパスワード*  
 A**文字列**新しいパスワードを指定する値。  
  
## <a name="remarks"></a>解説  
 セキュリティ上の理由には、新しいパスワードに加え、古いパスワードを指定してください。  
  
 プロバイダーが trustee プロパティの管理をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [ユーザー オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [グループとユーザーの追加、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)

