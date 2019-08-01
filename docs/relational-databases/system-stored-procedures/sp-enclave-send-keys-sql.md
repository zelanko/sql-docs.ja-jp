---
title: sp_enclave_send_keys (Transact-sql) |Microsoft Docs
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
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b4ced2feee2227ba1db492f721f57907069c5d99
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661359"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys (Transact-sql)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

データベース内のエンクレーブが有効なすべての列暗号化キーを、 [secure enclaves &#40;&#41;データベースエンジンの Always Encrypted](../../relational-databases/security/encryption/always-encrypted-enclaves.md)によって使用されるエンクレーブに送信します。

## <a name="syntax"></a>構文  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>引数

このストアドプロシージャには引数がありません。

## <a name="return-value"></a>戻り値

このストアドプロシージャには戻り値がありません。
  
## <a name="result-sets"></a>結果セット

このストアドプロシージャには結果セットがありません。
  
## <a name="remarks"></a>コメント

次のすべての条件が満たされている場合、 **sp_enclave_send_keys**はエンクレーブが有効な列暗号化キーをエンクレーブに送信します。

- エンクレーブは、SQL Server インスタンスで有効になっています。
- **sp_enclave_send_keys**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントドライバーを使用してアプリケーションから呼び出され、Always Encrypted とエンクレーブの両方の計算が有効になっているデータベース接続を使用して、secure enclaves の Always Encrypted をサポートしています。

## <a name="permissions"></a>アクセス許可

 データベースで、 **VIEW ANY COLUMN ENCRYPTION KEY definition**および**VIEW ANY COLUMN MASTER key definition**権限が必要です。  
  
## <a name="examples"></a>使用例  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>関連項目

 [Secure enclaves &#40;データベースエンジンでの Always Encrypted&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [チュートリアル: ランダム化された暗号化を使用したエンクレーブ対応列でのインデックスの作成と使用](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [キャッシュされた列暗号化キーを使用したインデックス作成操作の呼び出し](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [ランダム化される暗号化を使用したエンクレーブ対応列のインデックス](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [AlwaysOn とデータベースの移行に関する考慮事項](../security/encryption/always-encrypted-enclaves.md#anchorname-1-considerations-availability-groups-db-migration)
