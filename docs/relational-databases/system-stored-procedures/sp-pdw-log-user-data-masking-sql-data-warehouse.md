---
title: "sp_pdw_log_user_data_masking (SQL データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-data-warehouse
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e401596add887d6bfc3f7fc7bd6b5255128b251c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  使用して**sp_pdw_log_user_data_masking**ユーザーのデータのマスキングを有効にする[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。 ユーザー データのマスキングでは、アプライアンス上のすべてのデータベースに対して、ステートメントに影響します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログを受けた**sp_pdw_log_user_data_masking**確実な[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。 **sp_pdw_log_user_data_masking**データベース トランザクション ログには影響しませんまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログ。  
  
 **背景知識:**既定の構成で[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログが完全に含む[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、および場合によってなどの操作に含まれているユーザー データを含める**挿入**、 **更新**、および**選択**ステートメントです。 アプライアンス上の問題が発生した場合は、分析、問題を再現するがなくても、問題の原因となった条件を許可します。 ユーザー データに書き込まれていることを防ぐために[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログ、お客様がこのストアド プロシージャを使用してユーザー データのマスキングを有効にするを選択できます。 ステートメントが引き続き書き込まれます[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティのログはすべて、いくつかの定義済みの定数値に置き換えられます。 ユーザー データを含む可能性のあるステートメント内のリテラルを隠蔽することができます。  
  
 アプライアンスの透過的なデータ暗号化が有効の場合は、ユーザーのデータのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログが自動的にオンにします。  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>パラメーター  
 [ **@masking_mode=** ] *masking_mode*  
 透過的なデータ暗号化ログ ユーザー データのマスキングが有効になっているかどうかを決定します。 *masking_mode*は**int**値は次のいずれかを指定できます。  
  
-   0 = 無効な場合、ユーザーに表示されるデータ、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。  
  
-   1 = 有効、ユーザーがデータのステートメントでの表示、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログは、ユーザー データをマスクします。  
  
-   2 = ステートメントには、ユーザー データを含むは書き込まれていない、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。  
  
 実行する**sp_pdw log_user_data_masking**パラメーターでは、TDE ログ ユーザー データのマスキングの現在の状態を返すスカラーの結果セットとしてアプライアンス上なくです。  
  
## <a name="remarks"></a>解説  
 ユーザーのデータのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティで定義済みの定数値を持つリテラルの置換を有効をログに記録**選択**DML ステートメントでは、ユーザー データを含めるようにします。 設定*masking_mode*を 1 にマスクしません、列名またはテーブル名などのメタデータ。 設定*masking_mode* 2 に列名またはテーブル名などのメタデータを持つステートメントを削除します。  
  
 ユーザーのデータのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログは次のように実装します。  
  
-   TDE とユーザー データのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティ ログは既定でオフにします。 ステートメントは自動的にマスクされないアプライアンスに、データベースの暗号化が有効でない場合。  
  
-   ユーザー データのマスキングをオンに自動的にアプライアンスで TDE を有効にする[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。  
  
-   TDE を無効にするには影響しませんユーザーのデータのマスキング[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]動作状況のログです。  
  
-   ユーザー データのマスキングでは、明示的に有効に[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]アクティビティ ログを使用して、 **sp_pdw_log_user_data_masking**プロシージャです。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **sysadmin**固定データベース ロール、または**CONTROL SERVER**権限です。  
  
## <a name="example"></a>例  
 次の例には、TDE のログ ユーザー データが、アプライアンスのマスクが可能です。  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>参照  
 [sp_pdw_database_encryption &#40;です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
