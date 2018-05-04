---
title: sp_helpmergedeleteconflictrows (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f7d2fc014ae372b07417d88513f964a6d7f4795f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  削除競合が失われたデータ行に関する情報を返します。 このストアド プロシージャは、集中管理されていない競合のログ記録が使用されたときに、パブリッシャー側のパブリケーション データベースまたはサブスクライバー側のサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%** です。 パブリケーションを指定した場合は、パブリケーションに関係するすべての競合が返されます。  
  
 [  **@source_object=**] **'***source_object***'**  
 ソース オブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**、既定値は NULL です。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。*パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。*publisher_db*は**sysname**、既定値は NULL です。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|削除競合のソース オブジェクトです。|  
|**rowguid**|**uniqueidentifier**|削除競合の行識別子 (ROWID) です。|  
|**conflict_type**|**int**|競合の種類を示すコードです。<br /><br /> **1** = UpdateConflict: 行レベルで競合が検出されました。<br /><br /> **2** = ColumnUpdateConflict: 列レベルで競合が検出されます。<br /><br /> **3** = UpdateDeleteWinsConflict: 削除競合で優先されます。<br /><br /> **4** = UpdateWinsDeleteConflict: 競合を避けるに削除された rowguid がこのテーブルに記録されます。<br /><br /> **5** = UploadInsertFailed: サブスクライバーからの挿入がパブリッシャーで適用できませんでした。<br /><br /> **6** = DownloadInsertFailed: パブリッシャーからの挿入がサブスクライバーで適用できませんでした。<br /><br /> **7** = UploadDeleteFailed: サブスクライバーでの削除がパブリッシャーにアップロードできませんでした。<br /><br /> **8** = DownloadDeleteFailed: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = UploadUpdateFailed: サブスクライバーでの更新がパブリッシャーで適用できませんでした。<br /><br /> **10** = DownloadUpdateFailed: パブリッシャーでの更新がサブスクライバーに適用できませんでした。|  
|**reason_code**|**Int**|状況依存のエラー コードです。|  
|**reason_text**|**varchar(720)**|状況依存のエラーの説明です。|  
|**origin_datasource**|**varchar(255)**|競合の元です。|  
|**pubid**|**uniqueidentifier**|パブリケーションの識別子です。|  
|**MSrepl_create_time**|**datetime**|競合情報が追加された時刻です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergedeleteconflictrows**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergedeleteconflictrows**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
