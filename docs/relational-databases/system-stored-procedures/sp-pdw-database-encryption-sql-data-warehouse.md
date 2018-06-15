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
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
caps.latest.revision: 8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: adb48589c9ba6268aa229cd21871504392151f8e
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703135"
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
  
  
