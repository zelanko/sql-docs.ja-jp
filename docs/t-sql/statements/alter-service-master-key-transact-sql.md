---
title: "ALTER SERVICE MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ALTER_SERVICE_MASTER_KEY_TSQL
- ALTER SERVICE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- FORCE option
- ALTER SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- modifying Service Master Key
- decryption [SQL Server], Service Master Key
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], modifying
ms.assetid: a1e9be0e-4115-47d8-9d3a-3316d876a35e
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ee9fd8a888ed796b4d01b007aec5f8217cce5d9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-service-master-key-transact-sql"></a>ALTER SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのサービス マスター _ キーを変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER SERVICE MASTER KEY   
    [ { <regenerate_option> | <recover_option> } ] [;]  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE  
  
<recover_option> ::=  
    { WITH OLD_ACCOUNT = 'account_name' , OLD_PASSWORD = 'password' }  
    |      
    { WITH NEW_ACCOUNT = 'account_name' , NEW_PASSWORD = 'password' }  
```  
  
## <a name="arguments"></a>引数  
 FORCE  
 データが失われる可能性があっても、サービス マスター キーを再生成することを示します。 詳細については、次を参照してください。 [SQL Server サービス アカウントを変更する](#_changing)このトピックで後述します。  
  
 REGENERATE  
 サービス マスター キーを再生成することを示します。  
  
 OLD_ACCOUNT **='***account_name***'**  
 古い Windows サービス アカウントの名前を指定します。  
  
> [!WARNING]  
>  このオプションは、互換性のために残されています。 使用しないでください。 使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager 代わりにします。  
  
 OLD_PASSWORD **='***パスワード***'**  
 古い Windows サービス アカウントのパスワードを指定します。  
  
> [!WARNING]  
>  このオプションは、互換性のために残されています。 使用しないでください。 使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager 代わりにします。  
  
 NEW_ACCOUNT **='***account_name***'**  
 新しい Windows サービス アカウントの名前を指定します。  
  
> [!WARNING]  
>  このオプションは、互換性のために残されています。 使用しないでください。 使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager 代わりにします。  
  
 新しい _ パスワード**='***パスワード***'**  
 新しい Windows サービス アカウントのパスワードを指定します。  
  
> [!WARNING]  
>  このオプションは、互換性のために残されています。 使用しないでください。 使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager 代わりにします。  
  
## <a name="remarks"></a>解説  
 サービス マスター キーは、リンク サーバーのパスワード、資格情報、またはデータベースのマスター キーの暗号化が最初に必要になったときに、自動的に生成されます。 サービス マスター キーは、ローカル コンピューターのキーまたは Windows Data Protection API を使用して暗号化されます。 この API は、の Windows 資格情報から派生したキーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] AES 暗号化アルゴリズムを使用してサービス マスター キー (SMK) とデータベース マスター キー (DMK) を保護します。 AES は、以前のバージョンで使用されていた 3DES よりも新しい暗号化アルゴリズムです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] にアップグレードした後で、マスター キーを AES にアップグレードするために SMK と DMK を再度生成する必要があります。 DMK を再作成する方法については、「[ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)」を参照してください。  
  
##  <a name="_changing"></a>SQL Server サービス アカウントの変更  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを変更するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、サービス アカウントの変更を管理するために、サービス マスター キーの冗長なコピーが保存されます。このコピーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループに与えられる必要な権限を持つコンピューター アカウントによって保護されます。 コンピューターを再構築した場合、以前にサービス アカウントによって使用されていたのと同じドメイン ユーザーがサービス マスター キーを復元できますが、 これは、ローカル アカウントまたは Local System、Local Service、またはネットワーク サービス アカウントでは機能しません。 移動する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別のコンピューターへのバックアップと復元を使用して、サービス マスター _ キーを移行します。  
  
 REGENERATE 句では、サービス マスター キーが再生成されます。 サービス マスター キーが再生成されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では古いサービス マスター キーで暗号化されていたすべてのキーの暗号化が解除され、それらのキーが新しいマスター キーで暗号化されます。 ただし、この操作はリソースを大量に消費するため、 キーのセキュリティに問題がある場合を除き、リソース要求が少ないときに実行するように考慮してください。 暗号化解除が 1 つでも失敗した場合は、ステートメント全体が失敗します。  
  
 FORCE オプションを使用すると、キーの再生成処理で現在のマスター キーを取得できなかった場合や、そのマスター キーで暗号化されている秘密キーをすべて暗号化解除できなかった場合でも、再生成処理が続行されます。 使用して、サービス マスター _ キーを復元できない FORCE 再生が失敗した場合にのみ使用して、 [RESTORE SERVICE MASTER KEY](../../t-sql/statements/restore-service-master-key-transact-sql.md)ステートメントです。  
  
> [!CAUTION]  
>  サービス マスター キーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 暗号化階層のルートになります。 サービス マスター キーでは、直接または間接的に、そのツリー内にある他のすべてのキーとシークレットが保護されます。 強制再生成で、依存関係のあるキーの暗号化を解除できなかった場合、そのキーで保護されているデータは失われます。  
  
 別のコンピューターに SQL を移動する場合、同じサービス アカウントを使用して SMK の暗号化を解除する必要があります。SQL Server では、自動的に、コンピューター アカウントの暗号化が修復されます。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、サービス マスター キーを再生成します。  
  
```  
ALTER SERVICE MASTER KEY REGENERATE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [RESTORE SERVICE MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-service-master-key-transact-sql.md)   
 [BACKUP SERVICE MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
