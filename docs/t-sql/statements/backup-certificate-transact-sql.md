---
title: BACKUP CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DUMP_CERTIFICATE_TSQL
- BACKUP CERTIFICATE
- sql13.swb.exportcertificate.f1
- DUMP CERTIFICATE
- BACKUP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- decryption [SQL Server], certificates
- exporting certificates
- certificates [SQL Server], exporting
- BACKUP CERTIFICATE statement
- backing up certificates [SQL Server]
- decryption [SQL Server]
- cryptography [SQL Server], certificates
ms.assetid: 509b9462-819b-4c45-baae-3d2d90d14a1c
caps.latest.revision: 40
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d8fad120755b75f9d7e07f9e10c184de6f879810
ms.sourcegitcommit: 9229fb9b37616e0b73e269d8b97c08845bc4b9f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2018
ms.locfileid: "39024268"
---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  証明書をファイルにエクスポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
BACKUP CERTIFICATE certname TO FILE = 'path_to_file'  
    [ WITH PRIVATE KEY   
      (   
        FILE = 'path_to_private_key_file' ,  
        ENCRYPTION BY PASSWORD = 'encryption_password'   
        [ , DECRYPTION BY PASSWORD = 'decryption_password' ]   
      )   
    ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>引数  
 *path_to_file*  
 証明書を保存するファイルの完全なパスを、ファイル名を含めて指定します。 ローカル パスまたはネットワーク上の場所を示す UNC パスを指定できます。 既定値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の DATA フォルダーのパスです。  
  
 *path_to_private_key_file*  
 秘密キーを保存するファイルの完全なパスを、ファイル名を含めて指定します。 ローカル パスまたはネットワーク上の場所を示す UNC パスを指定できます。 既定値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の DATA フォルダーのパスです。  
  
 *encryption_password*  
 バックアップ ファイルに秘密キーを書き込む前に、キーを暗号化するため使用するパスワードを指定します。 パスワードに対しては、複雑性がチェックされます。  
  
 *decryption_password*  
 秘密キーをバックアップする前に、秘密キーの暗号化を解除するため使用するパスワードを指定します。 証明書がマスター キーによって暗号化されている場合、これは必要はありません。 
  
## <a name="remarks"></a>Remarks  
 データベースで秘密キーがパスワードによって暗号化されている場合は、暗号化解除パスワードを指定する必要があります。  
  
 秘密キーをファイルにバックアップする場合は、暗号化が必要です。 バックアップした証明書の保護に使用するパスワードは、証明書の秘密キーの暗号化に使用するパスワードとは異なります。  
  
 バックアップした証明書を復元するには、[CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md) ステートメントを使います。
 
 バックアップを実行すると、ファイルは SQL Server インスタンスのサービス アカウントに対して ACL されます。 別のアカウントで実行しているサーバーに証明書を復元する必要がある場合は、ファイルに対するアクセス許可を調整して、新しいアカウントでファイルの読み取りを実行できるようにする必要があります。 
  
## <a name="permissions"></a>アクセス許可  
 証明書に対する CONTROL 権限と、秘密キーの暗号化に使用するパスワードの情報が必要です。 証明書のパブリックの部分だけをバックアップする場合は、証明書の権限が必要です。また、呼び出し元に対して証明書の VIEW 権限が拒否されていないことも必要になります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-exporting-a-certificate-to-a-file"></a>A. 証明書をファイルにエクスポートする  
 次の例では、証明書をファイルにエクスポートします。  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert';  
GO  
```  
  
### <a name="b-exporting-a-certificate-and-a-private-key"></a>B. 証明書と秘密キーをエクスポートする  
 次の例では、バックアップする証明書の秘密キーをパスワード `997jkhUbhk$w4ez0876hKHJH5gh` で暗号化します。  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = 'c:\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
### <a name="c-exporting-a-certificate-that-has-an-encrypted-private-key"></a>C. 秘密キーが暗号化されている証明書をエクスポートする  
 次の例では、データベースで証明書の秘密キーが暗号化されています。 この秘密キーは、パスワード `9875t6#6rfid7vble7r` を使って暗号化を解除する必要があります。 証明書をバックアップ ファイルに保存するときには、秘密キーをパスワード `9n34khUbhk$w4ecJH5gh` で暗号化します。  
  
```  
BACKUP CERTIFICATE sales09 TO FILE = 'c:\storedcerts\sales09cert'   
    WITH PRIVATE KEY ( DECRYPTION BY PASSWORD = '9875t6#6rfid7vble7r' ,  
    FILE = 'c:\storedkeys\sales09key' ,   
    ENCRYPTION BY PASSWORD = '9n34khUbhk$w4ecJH5gh' );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)  
  
  

