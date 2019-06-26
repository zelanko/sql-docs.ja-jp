---
title: sp_enclave_send_keys (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enclave_send_keys
- sp_enclave_send_keys_TSQL
- sys.sp_enclave_send_keys
- sys.sp_enclave_send_keys_TSQL
helpviewer_keywords:
- sp_enclave_send_keys
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6540cdd36cccba4f5a7ccb3beddf31ce00cd9107
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394144"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

使用されるエンクレーブにデータベースのエンクレーブが有効な列暗号化キーを送信[セキュリティで保護された enclaves で Always Encrypted&#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)します。

## <a name="syntax"></a>構文  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>引数

このストアド プロシージャに引数がありません。

## <a name="return-value"></a>戻り値

このストアド プロシージャには、戻り値はありません。
  
## <a name="result-sets"></a>結果セット

このストアド プロシージャには、結果セットがありません。
  
## <a name="remarks"></a>コメント

**sp_enclave_send_keys**のすべての次の条件が満たされた場合、エンクレーブ対応の列暗号化キーをエンクレーブに送信します。

- エンクレーブは、SQL Server インスタンスで有効です。
- **sp_enclave_send_keys**を使用して、アプリケーションから呼び出されていますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ドライバーで Always Encrypted のサポートを有効になっている Always Encrypted とエンクレーブ計算を持つデータベース接続を使用してセキュリティで保護された enclaves でします。

## <a name="permissions"></a>アクセス許可

 必要な**VIEW ANY COLUMN ENCRYPTION KEY DEFINITION**と**VIEW ANY COLUMN MASTER KEY DEFINITION**データベースのアクセス許可。  
  
## <a name="examples"></a>使用例  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>関連項目

 [セキュリティで保護された enclaves で always Encrypted&#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [チュートリアル: 作成して、ランダム化された暗号化を使用して、エンクレーブ対応の列にインデックスを使用](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [キャッシュされた列暗号化キーを使用してインデックス作成操作を呼び出す](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [ランダムな暗号化を使用して、エンクレーブ対応の列のインデックス](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [AlwaysOn とデータベースの移行に関する考慮事項](../security/encryption/always-encrypted-enclaves.md#considerations-for-alwayson-and-database-migration)
