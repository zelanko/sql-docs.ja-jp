---
title: sp_helpmergedeleteconflictrows (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 270ca534b5527efa9dea52b107166bb445965b2f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595680"
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
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%** します。 パブリケーションを指定した場合は、パブリケーションに関係するすべての競合が返されます。  
  
 [  **@source_object=**] **'***source_object***'**  
 ソース オブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**、既定値は NULL です。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。*パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。*publisher_db*は**sysname**、既定値は NULL です。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
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
  
## <a name="remarks"></a>コメント  
 **sp_helpmergedeleteconflictrows**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergedeleteconflictrows**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
