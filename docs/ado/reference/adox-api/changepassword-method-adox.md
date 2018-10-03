---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96268fac4b81230fcb63db6b48ef4ef794abb9c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788710"
---
# <a name="changepassword-method-adox"></a>ChangePassword メソッド (ADOX)
パスワードを変更、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)アカウント。  
  
## <a name="syntax"></a>構文  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>パラメーター  
 *OldPassword*  
 A**文字列**ユーザーの既存のパスワードを指定する値。 ユーザーがパスワードを持っていない現在場合、使用して、空の文字列 ("") の*OldPassword*します。  
  
 *NewPassword*  
 A**文字列**新しいパスワードを指定する値。  
  
## <a name="remarks"></a>コメント  
 セキュリティ上の理由から、新しいパスワードだけでなく、古いパスワードを指定してください。  
  
 プロバイダーがデータ保護受託者プロパティの管理をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Groups および Users Append、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
