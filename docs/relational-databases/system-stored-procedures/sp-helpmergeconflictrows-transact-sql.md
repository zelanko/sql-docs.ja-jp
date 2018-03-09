---
title: "sp_helpmergeconflictrows (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1658eea769d134222e673269084511ae1222057
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された競合テーブルの行を返します。 このストアド プロシージャは、競合テーブルが格納されているコンピューター上で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%**です。 パブリケーションを指定した場合は、パブリケーションに関係するすべての競合が返されます。 たとえば場合、 **MSmerge_conflict_Customers**テーブルが競合する行を**WA**と**CA**パブリケーションの場合、パブリケーション名を渡す**CA**に関連する競合の取得、 **CA**パブリケーション。  
  
 [  **@conflict_table=**] **'***conflict_table***'**  
 競合テーブルの名前を指定します。 *conflict_table*は**sysname**、既定値はありません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンで競合テーブルがという名前の形式名を使用して **msmerge_conflict _*パブリケーション*_*記事** *、1 つのテーブルのパブリッシュされた各アーティクルです。  
  
 [  **@publisher=**] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。*publisher_db*は**sysname**、既定値は NULL です。  
  
 [  **@logical_record_conflicts=** ] *logical_record_conflicts*  
 結果セットに論理レコードの競合に関する情報を含めるかどうかを指定します。 *logical_record_conflicts*は**int**既定値は 0 です。 **1**論理レコード競合情報が返されることを意味します。  
  
## <a name="result-sets"></a>結果セット  
 **sp_helpmergeconflictrows**結果ベース テーブルの構造とこれらの追加列から成るセットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar (255)**|競合の元です。|  
|**conflict_type**|**int**|競合のタイプを示すコード。<br /><br /> **1** = 更新の競合: 行レベルで競合が検出されました。<br /><br /> **2** = 列更新の競合: 列レベルで検出された競合します。<br /><br /> **3** = 更新削除 Wins の競合: 削除競合で優先されます。<br /><br /> **4** = 更新 Wins の削除の競合: 競合を避けるに削除された rowguid がこのテーブルに記録されます。<br /><br /> **5** = 挿入のアップロードの失敗: サブスクライバーからの挿入がパブリッシャーで適用できませんでした。<br /><br /> **6** = 挿入のダウンロードに失敗: サブスクライバーでパブリッシャーからの挿入を適用できませんでした。<br /><br /> **7** = アップロード削除に失敗: サブスクライバーでの削除がパブリッシャーにアップロードできませんでした。<br /><br /> **8** = 削除のダウンロードに失敗: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = アップロード更新失敗: パブリッシャー、サブスクライバーでの更新を適用できませんでした。<br /><br /> **10** = 更新のダウンロードに失敗: パブリッシャーでの更新がサブスクライバーに適用できませんでした。<br /><br /> **12** = 論理レコードの更新が優先 Delete: 削除された論理レコード競合を避けるはこのテーブルに記録されます。<br /><br /> **13** = 論理レコード競合挿入を更新します。 論理レコードを挿入、更新プログラムに競合しています。<br /><br /> **14** = 論理レコードの削除が優先更新の競合: 競合を避ける更新された論理レコードはこのテーブルに記録されます。|  
|**reason_code**|**int**|状況依存のエラー コードです。|  
|**reason_text**|**varchar(720)**|状況依存のエラーの説明です。|  
|**pubid**|**uniqueidentifier**|パブリケーションの識別子です。|  
|**MSrepl_create_time**|**datetime**|競合情報が追加された時刻です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergeconflictrows**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、および**replmonitor** を実行できるは、ディストリビューションデータベースにロール**sp_helpmergeconflictrows**です。  
  
## <a name="see-also"></a>参照  
 [マージ パブリケーション &#40; の競合情報の表示レプリケーション TRANSACT-SQL プログラミング &#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
