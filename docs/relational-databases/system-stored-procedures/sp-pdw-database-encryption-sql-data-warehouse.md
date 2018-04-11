---
title: sp_pdw_database_encryption (SQL データ ウェアハウス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e63022bd135d7c5fc78dd717b6a0bdd27dc5311
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  使用して**sp_pdw_database_encryption**での透過的なデータ暗号化を有効にする、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アプライアンスです。 ときに**sp_pdw_database_encryption**を 1、使用する設定、 **ALTER DATABASE** TDE を使用してデータベースを暗号化するステートメント。  
  
## <a name="syntax"></a>構文  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>パラメーター  
 [ **@enabled=** ] *enabled*  
 透過的なデータ暗号化が有効になっているかどうかを判断します。 *有効になっている*は**int**値は次のいずれかを指定できます。  
  
-   0 = 無効  
  
-   1 = 有効  
  
 実行する**sp_pdw_database_encryption**パラメーターでは、TDE の現在の状態を返すスカラーの結果セットとしてアプライアンス上なく: 無効の場合、0 または 1 を有効にします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 使用して、TDE が有効にすると**sp_pdw_database_encryption**、tempdb データベースの削除、再作成および暗号化します。 そのためは、TDE を有効にアプライアンスでは、tempdb を使用してアクティブなセッションはその他のことはできません。 有効化またはアプライアンスで TDE を無効にすると、ほとんどの場合、アプライアンスの状態を変更する操作アプライアンスの有効期間に 1 度だけ実行する予定がアプライアンス上のトラフィックがない場合に実行する必要があります。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **sysadmin**固定データベース ロール、または**CONTROL SERVER**権限です。  
  
## <a name="example"></a>例  
 次の例では、アプライアンス上 TDE が有効です。  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>参照  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
