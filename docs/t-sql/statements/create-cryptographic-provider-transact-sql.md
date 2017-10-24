---
title: "暗号化サービス プロバイダー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_CRYPTOGRAPHIC_TSQL
- CRYPTOGRAPHIC PROVIDER
- PROVIDER_TSQL
- CREATE CRYPTOGRAPHIC
- CREATE CRYPTOGRAPHIC PROVIDER
- CRYPTOGRAPHIC_PROVIDER_TSQL
- CREATE_CRYPTOGRAPHIC_PROVIDER_TSQL
- PROVIDER
dev_langs:
- TSQL
helpviewer_keywords:
- 33085 (Database Engine error)
- CREATE CRYPTOGRAPHIC PROVIDER statement
- 33032 (Database Engine error)
ms.assetid: 059a39a6-9d32-4d3f-965b-0a1ce75229c7
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a7252786522ef4e0b4206db06d7dc8aa76cf308
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-cryptographic-provider-transact-sql"></a>CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内で、暗号化サービス プロバイダー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張キー管理 (EKM) プロバイダーからです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE CRYPTOGRAPHIC PROVIDER provider_name   
    FROM FILE = path_of_DLL  
```  
  
## <a name="arguments"></a>引数  
 *provider_name*  
 拡張キー管理プロバイダーの名前を指定します。  
  
 *path_of_DLL*  
 実装する .dll ファイルのパス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張キー管理インターフェイスです。 使用する場合、 **SQL Server コネクタ for Microsoft Azure Key Vault**既定の場所は**' C:\Program files \microsoft SQL Server コネクタの Microsoft Azure キー Vault\Microsoft.AzureKeyVaultService.EKM.dll'**.  
  
## <a name="remarks"></a>解説  
 プロバイダーによって作成されるキーはいずれも、プロバイダーをその GUID で参照します。 GUID は、DLL のすべてのバージョン間で保持されます。  
  
 SQLEKM インターフェイスを実装する DLL は、任意の証明書を使用して、デジタル署名する必要があります。 この署名は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって検証されます。 これには、その証明書チェーン、そのルートにインストールされている必要がありますが含まれます、 **Trusted Root Cert Authorities** Windows システム上の場所。 署名が正しく検証されない場合は、CREATE CRYPTOGRAPHIC PROVIDER ステートメントは失敗します。 証明書および証明書チェーンの詳細については、次を参照してください。 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)です。  
  
 EKM プロバイダーの dll で必要なメソッドの一部が実装されなかった場合は、CREATE CRYPTOGRAPHIC PROVIDER から次のエラー 33085 が返されることがあります。  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
 EKM プロバイダーの dll の作成に使用されたヘッダー ファイルが古い場合は、CREATE CRYPTOGRAPHIC PROVIDER から次のエラー 33032 が返されることがあります。  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限またはメンバーシップが必要、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれる暗号化サービス プロバイダーを作成する`SecurityProvider`で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].dll ファイルからです。 .Dll ファイルの名前は`c:\SecurityProvider\SecurityProvider_v1.dll`サーバーにインストールされているとします。 最初にプロバイダーの証明書をサーバーにインストールする必要があります。  
  
```  
-- Install the provider  
CREATE CRYPTOGRAPHIC PROVIDER SecurityProvider  
    FROM FILE = 'C:\SecurityProvider\SecurityProvider_v1.dll';  
```  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  

