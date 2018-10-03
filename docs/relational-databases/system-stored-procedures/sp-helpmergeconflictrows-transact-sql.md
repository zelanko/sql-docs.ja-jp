---
title: sp_helpmergeconflictrows (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26bf2e89462c0096c9a6fd2a081cb72c68e9a32a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746580"
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
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%** します。 パブリケーションを指定した場合は、パブリケーションに関係するすべての競合が返されます。 たとえば場合、 **MSmerge_conflict_Customers**テーブルが競合する行を**WA**と**CA**パブリケーション、パブリケーション名を渡して**CA**に関連する競合の取得、 **CA**パブリケーション。  
  
 [  **@conflict_table=**] **'***conflict_table***'**  
 競合テーブルの名前を指定します。 *conflict_table*は**sysname**、既定値はありません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と以降のバージョンで競合テーブルの名前付けの形式名を使用して **msmerge_conflict _* パブリケーション *_* 記事 * * *、パブリッシュされた各テーブルを使用アーティクルです。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。*publisher_db*は**sysname**、既定値は NULL です。  
  
 [  **@logical_record_conflicts=** ] *logical_record_conflicts*  
 結果セットに論理レコードの競合に関する情報を含めるかどうかを指定します。 *logical_record_conflicts*は**int**既定値は 0 です。 **1**論理レコードの競合情報が返されることを意味します。  
  
## <a name="result-sets"></a>結果セット  
 **sp_helpmergeconflictrows**結果ベース テーブルの構造とこれらの列で構成されるセットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|競合の元です。|  
|**conflict_type**|**int**|競合のタイプを示すコード。<br /><br /> **1** = 更新の競合: 行レベルで競合が検出されました。<br /><br /> **2** = 列更新の競合: 列レベルで検出された競合します。<br /><br /> **3** = 更新プログラムの削除が優先される競合: 競合で削除が優先されます。<br /><br /> **4** = 更新 Wins の削除の競合: 競合を避けるに削除された rowguid がこのテーブルに記録されます。<br /><br /> **5** = 挿入のアップロードの失敗: サブスクライバーからの挿入がパブリッシャーで適用できませんでした。<br /><br /> **6** = 挿入のダウンロードに失敗: パブリッシャーからの挿入がサブスクライバーで適用できませんでした。<br /><br /> **7** = アップロードの削除に失敗: サブスクライバーでの削除がパブリッシャーにアップロードできませんでした。<br /><br /> **8** = 削除のダウンロードに失敗: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = アップロードの更新に失敗: サブスクライバーでの更新がパブリッシャーで適用できませんでした。<br /><br /> **10** = 更新のダウンロードに失敗: パブリッシャーでの更新をサブスクライバーに適用できませんでした。<br /><br /> **12** = 論理レコードの更新が優先削除: 削除された論理レコード競合を避けるがこのテーブルに記録されます。<br /><br /> **13** = 論理レコード競合挿入更新: 更新プログラムと競合して論理レコードを挿入します。<br /><br /> **14** = 論理レコードの削除が優先更新の競合: 競合を避ける論理レコードの更新がこのテーブルに記録されます。|  
|**reason_code**|**int**|状況依存のエラー コードです。|  
|**reason_text**|**varchar(720)**|状況依存のエラーの説明です。|  
|**pubid**|**uniqueidentifier**|パブリケーションの識別子です。|  
|**MSrepl_create_time**|**datetime**|競合情報が追加された時刻です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpmergeconflictrows**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーだけ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、および**replmonitor** を実行できるは、ディストリビューションデータベースでロール**sp_helpmergeconflictrows**します。  
  
## <a name="see-also"></a>参照  
 [マージ パブリケーションの競合情報の表示&#40;レプリケーション TRANSACT-SQL プログラミング&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
