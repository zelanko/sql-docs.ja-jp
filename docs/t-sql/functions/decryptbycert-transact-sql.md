---
title: DECRYPTBYCERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87a3b0cf3db642100dc65fc4a534e9af82b57852
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  証明書の秘密キーを使ってデータの暗号化を解除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>引数  
 *certificate_ID*  
 データベース内の証明書の ID を指定します。 *certificate*_ID は **int**です。  
  
 *ciphertext*  
 証明書の公開キーで暗号化されているデータの文字列を指定します。  
  
 @ciphertext  
 証明書を使用して暗号化されているデータを含む **varbinary** 型の変数を指定します。  
  
 *cert_password*  
 証明書の秘密キーの暗号化に使用されたパスワードを指定します。 Unicode であることが必要です。  
  
 @cert_password  
 証明書のプライベート キーを暗号化するために指定されたパスワードを含む **nchar** または **nvarchar** を指定します。 Unicode であることが必要です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>Remarks  
 この関数では、証明書の秘密キーを使ってデータの暗号化を解除します。 非対称キーを使用する暗号化変換では、リソースが大幅に消費されます。 このため、ユーザー データを日常的に暗号化する場合、EncryptByCert および DecryptByCert は適切ではありません。  
  
## <a name="permissions"></a>アクセス許可  
 証明書に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`[AdventureWorks2012].[ProtectedData04]` とマークされた `data encrypted by certificate JanainaCert02` から行を選択し、 証明書 `JanainaCert02` の秘密キーを使って暗号化を解除します。最初に証明書のパスワード `pGFD4bb925DGvbd2439587y` を使って証明書の暗号化を解除する必要があります。 復号化されたデータを変換 **varbinary** に **nvarchar**です。  
  
```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
