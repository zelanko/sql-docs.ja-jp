---
title: "BACKUP MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
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
- BACKUP MASTER KEY
- DUMP_MASTER_KEY_TSQL
- BACKUP_MASTER_KEY_TSQL
- DUMP MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- BACKUP MASTER KEY statement
- exporting Database Master Keys
- encryption [SQL Server], Database Master Key
- cryptography [SQL Server], Database Master Key
- backing up master keys [SQL Server]
- database master key [SQL Server], exporting
ms.assetid: 0e25fe22-2536-4d7e-ba4a-1921e880f367
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2caa8c920794d002adc3f75ee760536c5cc7acc8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="backup-master-key-transact-sql"></a>BACKUP MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースのマスター キーをエクスポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
BACKUP MASTER KEY TO FILE = 'path_to_file'   
    ENCRYPTION BY PASSWORD = 'password'  
```  
  
## <a name="arguments"></a>引数  
 ファイル ='*path_to_file*'  
 マスター キーのエクスポート先ファイルの完全なパスを、ファイル名を含めて指定します。 これには、ローカル パスまたはネットワーク上の場所への UNC パスがあります。  
  
 パスワード ='*パスワード*'  
 ファイル内のマスター キーの暗号化に使用されているパスワードを指定します。 このパスワードに対しては、複雑性がチェックされます。 詳細については、「 [Password Policy](../../relational-databases/security/password-policy.md)」をご参照ください。  
  
## <a name="remarks"></a>解説  
 マスター キーは開かれている必要があります。したがって、バックアップ前に暗号化を解除する必要があります。 マスター キーがサービス マスター キーで暗号化されている場合は、明示的に開く必要はありません。 パスワードのみで暗号化されている場合は、明示的に開く必要があります。  
  
 マスター キーは作成後すぐにバックアップし、安全な別の場所に保存することをお勧めします。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdventureWorks2012` マスター キーのバックアップを作成します。 このマスター キーはサービス マスター キーによって暗号化されているので、マスター キーを開くときにはパスワードを指定する必要があります。  
  
```  
USE AdventureWorks2012;  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';  
BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
    ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';  
GO   
```  
  
## <a name="see-also"></a>参照  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [MASTER KEY &#40; を開くTRANSACT-SQL と #41 です。](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/close-master-key-transact-sql.md)   
 [RESTORE MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
