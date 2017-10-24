---
title: "OPEN SYMMETRIC KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPEN SYMMETRIC KEY
- OPEN_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], opening
- OPEN SYMMETRIC KEY statement
ms.assetid: ff019a7c-c373-46c7-ac43-ffb7e2ee60b3
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd8302417e09eeef6e8052db6ced58c47cd25158
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="open-symmetric-key-transact-sql"></a>OPEN SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  対称キーの暗号化を解除し、対称キーを使用可能にします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OPEN SYMMETRIC KEY Key_name DECRYPTION BY <decryption_mechanism>  
  
<decryption_mechanism> ::=  
    CERTIFICATE certificate_name [ WITH PASSWORD = 'password' ]  
    |  
    ASYMMETRIC KEY asym_key_name [ WITH PASSWORD = 'password' ]  
    |  
    SYMMETRIC KEY decrypting_Key_name  
    |  
    PASSWORD = 'decryption_password'  
```  
  
## <a name="arguments"></a>引数  
 *Key_name*  
 開く対称キーの名前を指定します。  
  
 証明書*certificate_name*  
 対称キーの暗号化解除に使用する秘密キーを備えた、証明書の名前を指定します。  
  
 非対称キー *asym_key_name*  
 対称キーの暗号化解除に使用する秘密キーを備えた、非対称キーの名前を指定します。  
  
 パスワード ='*パスワード*'  
 証明書の秘密キーまたは非対称キーの暗号化に使用されているパスワードを指定します。  
  
 対称キー *decrypting_key_name*  
 開く対称キーの暗号化解除に使用する対称キーの名前を指定します。  
  
 パスワード ='*パスワード*'  
 対称キーの保護に使用されているパスワードを指定します。  
  
## <a name="remarks"></a>解説  
 開いている対称キーは、セキュリティ コンテキストではなくセッションにバインドされており、 明示的に閉じられるか、セッションが終了するまで引き続き使用できます。 対称キーを開いてからコンテキストを切り替えた場合、キーは開かれたままになり、権限を借用したコンテキストでも使用できます。 開いている対称キーに関する情報は、 [sys.openkeys & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md)カタログ ビューです。  
  
 対称キーが別のキーで暗号化された場合は、そのキーを最初に開く必要があります。  
  
 対称キーを既に開いている場合、クエリは、 **NO_OP**です。  
  
 対称キーの暗号化解除に指定したパスワード、証明書、またはキーが正しくない場合、クエリは失敗します。  
  
 暗号化プロバイダーから作成された対称キーは、開くことはできません。 この種の対称キーを使用して暗号化および暗号化解除の操作が成功せず、**開く**ステートメント、暗号化サービス プロバイダーを開くと、キーを閉じるためです。  
  
## <a name="permissions"></a>Permissions  
 呼び出し元にはキーに対する権限が必要です。キーに対する VIEW DEFINITION 権限が拒否されていないことも必要になります。 また、暗号化解除メカニズムに応じた追加要件があります。  
  
-   DECRYPTION BY CERTIFICATE の場合は、証明書に対する CONTROL 権限と、秘密キーを暗号化したパスワードの情報が必要です。  
  
-   DECRYPTION BY ASYMMETRIC KEY の場合は、非対称キーに対する CONTROL 権限と、秘密キーを暗号化したパスワードの情報が必要です。  
  
-   DECRYPTION BY PASSWORD の場合は、対称キーの暗号化に使用されたパスワードの 1 つについての情報が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-opening-a-symmetric-key-by-using-a-certificate"></a>A. 証明書を使用して対称キーを開く  
 次の例では、対称キー `SymKeyMarketing3` を開き、証明書 `MarketingCert9` の秘密キーを使って暗号化を解除します。  
  
```  
USE AdventureWorks2012;  
OPEN SYMMETRIC KEY SymKeyMarketing3   
    DECRYPTION BY CERTIFICATE MarketingCert9;  
GO  
```  
  
### <a name="b-opening-a-symmetric-key-by-using-another-symmetric-key"></a>B. 別の対称キーを使用して対称キーを開く  
 次の例は、対称キーを開きます`MarketingKey11`対称キーを使用して暗号化を解除して`HarnpadoungsatayaSE3`です。  
  
```  
USE AdventureWorks2012;  
-- First open the symmetric key that you want for decryption.  
OPEN SYMMETRIC KEY HarnpadoungsatayaSE3   
    DECRYPTION BY CERTIFICATE sariyaCert01;  
-- Use the key that is already open to decrypt MarketingKey11.  
OPEN SYMMETRIC KEY MarketingKey11   
    DECRYPTION BY SYMMETRIC KEY HarnpadoungsatayaSE3;  
GO   
```  
  
## <a name="see-also"></a>参照  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  

