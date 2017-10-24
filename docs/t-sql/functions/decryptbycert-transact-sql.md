---
title: "DECRYPTBYCERT (TRANSACT-SQL) |Microsoft ドキュメント"
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ebdc328e49635af823cd64e8539ee5b7cfa95c76
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  証明書の秘密キーを使ってデータの暗号化を解除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>引数  
 *certificate_ID*  
 データベース内の証明書の ID を指定します。 *証明書*_id のデータ型は**int**です。  
  
 *暗号化テキスト*  
 証明書の公開キーで暗号化されているデータの文字列を指定します。  
  
 @ciphertext  
 型の変数は、 **varbinary**証明書で暗号化されたデータが含まれます。  
  
 *cert_password*  
 証明書の秘密キーの暗号化に使用されたパスワードを指定します。 Unicode であることが必要です。  
  
 @cert_password  
 型の変数は、 **nchar**または**nvarchar**証明書の秘密キーの暗号化に使用されたパスワードを格納しています。 Unicode であることが必要です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>解説  
 この関数では、証明書の秘密キーを使ってデータの暗号化を解除します。 非対称キーを使用する暗号化変換では、リソースが大幅に消費されます。 このため、ユーザー データを日常的に暗号化する場合、EncryptByCert および DecryptByCert は適切ではありません。  
  
## <a name="permissions"></a>Permissions  
 証明書に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例から行を選択する`[AdventureWorks2012].[ProtectedData04]`とマークされている`data encrypted by certificate JanainaCert02`です。 例では、証明書の秘密キーで暗号化を解除する`JanainaCert02`、まず、証明書のパスワードを使用して復号化`pGFD4bb925DGvbd2439587y`です。 復号化されたデータを変換**varbinary**に**nvarchar**です。  
  
```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ENCRYPTBYCERT および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [証明書 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

