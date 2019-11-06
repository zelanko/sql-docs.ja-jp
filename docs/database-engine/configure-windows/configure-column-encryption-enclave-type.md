---
title: Column encryption enclave type サーバー構成オプション |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: ec0b088d7ed1f32661a9ca171eb5f889c09ae5d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68012800"
---
# <a name="column-encryption-enclave-type-server-configuration-option"></a>Column encryption enclave type サーバー構成オプション
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  **column encryption enclave type** (列暗号化エンクレーブの型) オプションを使用すると、Always Encrypted のセキュア エンクレーブを有効または無効にすることができます。  詳細については、「[セキュア エンクレーブを使用する Always Encrypted](../../relational-databases/security/encryption/always-encrypted-enclaves.md)」を参照してください。

 **column encryption enclave type** で指定できる値は次の表のとおりです。  
  
|[値]|Description|  
|-------------------|-----------------|  
|0|**セキュア エンクレーブなし**。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は Always Encrypted のセキュア エンクレーブを初期化しません。 そのため、セキュア エンクレーブを使用した Always Encrypted の機能は利用できなくなります。|  
|1|**仮想化ベースのセキュリティ (VBS)** 。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は Always Encrypted のセキュア エンクレーブ (VBS セキュア メモリ エンクレーブ) を初期化します。|    

> [!IMPORTANT]
> **column encryption enclave type** の変更は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動するまで反映されません。
  
   
## <a name="examples"></a>使用例  
 次に示すのは、セキュア エンクレーブを有効にする場合の例です。  

```sql  
sp_configure 'column encryption enclave type', 1;  
GO  
RECONFIGURE;  
GO  
```  

次に示すのは、セキュア エンクレーブを無効にする場合の例です。  

```sql  
sp_configure 'column encryption enclave type', 0;  
GO  
RECONFIGURE;  
GO  
```  

## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
