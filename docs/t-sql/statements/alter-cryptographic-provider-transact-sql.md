---
title: "ALTER CRYPTOGRAPHIC PROVIDER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_CRYPTOGRAPHIC_PROVIDER_TSQL
- ALTER CRYPTOGRAPHIC PROVIDER
- ALTER_CRYPTOGRAPHIC_TSQL
- ALTER CRYPTOGRAPHIC
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER CRYPTOGRAPHIC PROVIDER
ms.assetid: 876b6348-fb29-49e1-befc-4217979f6416
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1579fb75de53747a26e647f69c7fc70346738fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-cryptographic-provider-transact-sql"></a>ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内の暗号プロバイダーを変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張キー管理 (EKM) プロバイダーからです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER CRYPTOGRAPHIC PROVIDER provider_name   
    [ FROM FILE = path_of_DLL ]  
    ENABLE | DISABLE  
```  
  
## <a name="arguments"></a>引数  
 *provider_name*  
 拡張キー管理プロバイダーの名前です。  
  
 *Path_of_DLL*  
 実装する .dll ファイルのパス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張キー管理インターフェイスです。  
  
 ENABLE | DISABLE  
 プロバイダーを有効にするか無効にするかを指定します。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で拡張キー管理を実装するために使用する .dll ファイルをプロバイダーから変更する場合、ALTER CRYPTOGRAPHIC PROVIDER ステートメントを使用する必要があります。  
  
 ALTER CRYPTOGRAPHIC PROVIDER ステートメントを使用して .dll ファイルのパスを更新すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では次の操作が実行されます。  
-   プロバイダーを無効にします。  
-   DLL の署名が、.dll ファイルの GUID がカタログに記録されているものと同じであることを確認します。  
-   カタログの DLL バージョンを更新します。  
  

EKM プロバイダーを DISABLE に設定した場合、新しく接続するときに、暗号化ステートメントでそのプロバイダーを使用しようとすると失敗します。  
  
プロバイダーを無効にするには、そのプロバイダーを使用するすべてのセッションを終了する必要があります。  
  
EKM プロバイダーの dll で必要なメソッドの一部が実装されなかった場合は、ALTER CRYPTOGRAPHIC PROVIDER から次のエラー 33085 が返されることがあります。  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
EKM プロバイダーの dll の作成に使用されたヘッダー ファイルが古い場合は、ALTER CRYPTOGRAPHIC PROVIDER から次のエラー 33032 が返されることがあります。  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 暗号化サービス プロバイダーに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれる、暗号化サービス プロバイダーを変更する`SecurityProvider`で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、.dll ファイルの新しいバージョンにします。 この新しいバージョンの名前は`c:\SecurityProvider\SecurityProvider_v2.dll`がサーバーにインストールされているとします。 プロバイダーの証明書をサーバーにインストールする必要があります。  
  
1. アップグレードを実行するプロバイダーを無効にします。 これは、開いているすべての暗号化セッションを終了します。  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
DISABLE;  
GO  
```  

2. プロバイダーの .dll ファイルをアップグレードします。 バージョンが異なる場合が、GUID では、以前のバージョンと同じ必要があります。  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider  
FROM FILE = 'c:\SecurityProvider\SecurityProvider_v2.dll';  
GO  
```  

3. アップグレード済みのプロバイダーを有効にします。   
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
ENABLE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  

