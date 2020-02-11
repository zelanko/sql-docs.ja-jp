---
title: sp_pdw_log_user_data_masking (SQL Data Warehouse) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 18798dece1c801ad0cc4854b7fccc15529a56d5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056452"
---
# <a name="sp_pdw_log_user_data_masking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  **Sp_pdw_log_user_data_masking**を使用して、アクティビティログ[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]でユーザーデータのマスキングを有効にします。 ユーザーデータのマスキングは、アプライアンス上のすべてのデータベースのステートメントに影響します。  
  
> [!IMPORTANT]  
>  **Sp_pdw_log_user_data_masking**によって影響を受けるアクティビティ[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ログは、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]特定のアクティビティログです。 **sp_pdw_log_user_data_masking**は、データベーストランザクションログまたはエラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログには影響しません。  
  
 **背景:** 既定の[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]構成アクティビティログには完全[!INCLUDE[tsql](../../includes/tsql-md.md)]なステートメントが含まれており、場合によっては**INSERT**、 **UPDATE**、 **SELECT**ステートメントなどの操作に含まれるユーザーデータが含まれます。 アプライアンスで問題が発生した場合は、問題の原因となった状況を分析して問題を再現する必要がありません。 ユーザーデータがアクティビティログに[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]書き込まれないようにするには、このストアドプロシージャを使用してユーザーデータのマスキングを有効にすることを選択できます。 ステートメントは引き続きアクティビティログに[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]書き込まれますが、ユーザーデータを含む可能性のあるステートメント内のすべてのリテラルがマスクされます。いくつかの定義済みの定数値に置き換えられます。  
  
 アプライアンスで transparent data encryption を有効にすると、アクティビティログ内[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]のユーザーデータのマスキングが自動的に有効になります。  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>パラメーター  
`[ @masking_mode = ] masking_mode`透過的なデータ暗号化ログユーザーデータのマスキングが有効かどうかを指定します。 *masking_mode*は**int**,、値は次のいずれかを指定することができます。  
  
-   0 = 無効。ユーザーデータは[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティログに表示されます。  
  
-   1 = 有効になっていると、ユーザー [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]データステートメントはアクティビティログに表示されますが、ユーザーデータはマスクされます。  
  
-   2 = ユーザーデータを含むステートメントは、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティログには書き込まれません。  
  
 パラメーターを指定せずに**sp_pdw_ log_user_data_masking**を実行すると、アプライアンス上の tde ログユーザーデータマスクの現在の状態がスカラー結果セットとして返されます。  
  
## <a name="remarks"></a>解説  
 ユーザーデータのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティログでは、ユーザーデータを含めることができる**SELECT**ステートメントと DML ステートメントで、定義済みの定数値を持つリテラルを置換できます。 *Masking_mode*を1に設定しても、列名やテーブル名などのメタデータはマスクされません。 *Masking_mode*を2に設定すると、列名やテーブル名などのメタデータを含むステートメントが削除されます。  
  
 アクティビティログでの[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ユーザーデータのマスキングは、次のように実装されます。  
  
-   既定では、アクティビティログの[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] tde とユーザーデータのマスキングはオフになっています。 アプライアンスでデータベース暗号化が有効になっていない場合、ステートメントは自動的にマスクされません。  
  
-   アプライアンスで TDE を有効にすると、アクティビティログの[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ユーザーデータのマスキングが自動的にオンになります。  
  
-   TDE を無効にしても、アクティビティ[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ログでのユーザーデータのマスキングには影響しません。  
  
-   Sp_pdw_log_user_data_masking の手順を使用して、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティログでユーザーデータ**** のマスキングを明示的に有効にすることができます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**固定データベースロールまたは**CONTROL SERVER**権限のメンバーシップが必要です。  
  
## <a name="example"></a>例  
 次の例では、TDE のログユーザーデータのマスキングを有効にします。  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>参照  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
