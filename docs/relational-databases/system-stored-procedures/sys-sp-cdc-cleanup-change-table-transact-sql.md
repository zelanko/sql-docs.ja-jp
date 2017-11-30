---
title: "sys.sp_cdc_cleanup_change_table (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_cleanup_change_table
- sp_cdc_cleanup_change_table_TSQL
- sys.sp_cdc_cleanup_change_table
- sys.sp_cdc_cleanup_change_table_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sp_cdc_cleanup_change_tables
- sp_cdc_cleanup_change_tables
ms.assetid: 02295794-397d-4445-a3e3-971b25e7068d
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8f81a229286a1226403d6d06aeca56fa13e8c60
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdccleanupchangetable-transact-sql"></a>sys.sp_cdc_cleanup_change_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに基づいて、指定された変更テーブルから行を削除*low_water_mark*値。 このストアド プロシージャは、変更テーブルのクリーンアップ プロセスを直接管理する必要のあるユーザーを想定して用意されています。 ただし、このプロシージャは、変更テーブルに含まれるデータのすべてのコンシューマーに影響を及ぼすため、使用する際は注意が必要です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_cleanup_change_table   
  [ @capture_instance = ] 'capture_instance',   
  [ @low_water_mark = ] low_water_mark ,  
  [ @threshold = ]'delete threshold'  
```  
  
## <a name="arguments"></a>引数  
 [ @capture_instance =] '*capture_instance*'  
 変更テーブルに関連付けられたキャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 *capture_instance*現在のデータベースに存在するキャプチャ インスタンス名を指定します。  
  
 [ @low_water_mark =] *low_water_mark*  
 新しい低水位マークとして使用するのには、ログ シーケンス番号 (LSN) は、*キャプチャ インスタンス*です。 *low_water_mark*は**binary (10)**、既定値はありません。  
  
 現在のエントリの start_lsn 値として表示される必要があります、値が null でない場合、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)テーブル。 cdc.lsn_time_mapping の他のエントリが、新しい低レベルのウォーターマークで識別されたエントリと同じコミット時間を共有する場合、そのグループのエントリに関連付けられた最小 LSN が低レベルのウォーターマークとして選択されます。  
  
 値が NULL の場合、現在を明示的に設定されている場合*低レベルのウォーターマーク*の*キャプチャ インスタンス*を使用してクリーンアップ操作の上限の境界を定義します。  
  
 [ @threshold=] '*しきい値を削除*'  
 クリーンアップ時に 1 つのステートメントを使用して削除できるエントリが削除の最大数です。 *delete_threshold*は**bigint**、既定値は 5000 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 sys.sp_cdc_cleanup_change_table は次の操作を実行します。  
  
1.  場合、@low_water_markパラメーターが NULL でない、start_lsn の値を設定、*キャプチャ インスタンス*を新しい*低レベルのウォーターマーク*です。  
  
    > [!NOTE]  
    >  新しい低レベルのウォーターマークは、ストアド プロシージャ呼び出しで指定されている低レベルのウォーターマークと異なる場合があります。 cdc.lsn_time_mapping テーブルの他のエントリが同じコミット時間を共有する場合、そのグループのエントリで表される最小の start_lsn が、調整された低レベルのウォーターマークとして選択されます。 場合、@low_water_markパラメーターが NULL または現在の低レベルのウォーターマークが新しい低より大きい、start_lsn 値は、キャプチャ インスタンスのままには変更されません。  
  
2.  変更テーブル エントリが持つ __$start_lsn の値が低レベルのウォーターマークより小さい場合は、その変更テーブル エントリが削除されます。 delete threshold を使用すると、1 つのトランザクションで削除される行の数を制限できます。 エントリを正常に削除できなかったときはエラーがレポートされます。ただし、呼び出しに基づいて行われた、キャプチャ インスタンスの低レベルのウォーターマークへの変更には影響はありません。  
  
 sys.sp_cdc_cleanup_change_table は、次のような場合に使用します。  
  
-   クリーンアップ エージェント ジョブで削除エラーがレポートされた場合  
  
     管理者は、このストアド プロシージャを明示的に実行して、失敗した操作を再試行できます。 指定したキャプチャ インスタンスのクリーンアップを再試行するには sys.sp_cdc_cleanup_change_table を実行し、NULL を指定する、@low_water_markパラメーター。  
  
-   クリーンアップ エージェント ジョブで使用される保有期間に基づく単純なポリシーが適さない場合  
  
     このストアド プロシージャは、単一のキャプチャ インスタンスに対してクリーンアップを実行します。このため、このストアド プロシージャを使用して、キャプチャ インスタンスごとにクリーンアップの規則が調整された、カスタムのクリーンアップ方法を構築することができます。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [cdc.fn_cdc_get_all_changes_ &#60; capture_instance &#62;。 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_get_min_lsn &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys.fn_cdc_increment_lsn &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
