---
title: MSmerge_conflicts_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34dd7496d514db14399134eb7ffe222af7251f95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737731"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflicts_info**テーブルはマージ パブリケーションに対するサブスクリプションを同期するときに発生する競合を追跡します。 競合行のデータが格納されている、 [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md)テーブル アーティクルの競合が発生しました。 このテーブルは、パブリッシャー側ではパブリケーション データベースに、サブスクライバー側ではサブスクリプション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネーム。|  
|**rowguid**|**uniqueidentifier**|競合している行の識別子です。|  
|**origin_datasource**|**nvarchar (255)**|競合している変更が発生したデータベースの名前です。|  
|**conflict_type**|**int**|発生した競合の種類です。次のいずれかの値をとります。<br /><br /> **1** = 更新の競合: 行レベルで競合が検出されました。<br /><br /> **2** = 列更新の競合: 列レベルで検出された競合します。<br /><br /> **3** = 更新プログラムの削除が優先される競合: 競合で削除が優先されます。<br /><br /> **4** = 更新 Wins の削除の競合: 競合を避けるに削除された rowguid がこのテーブルに記録されます。<br /><br /> **5** = 挿入のアップロードの失敗: サブスクライバーからの挿入がパブリッシャーで適用できませんでした。<br /><br /> **6** = 挿入のダウンロードに失敗: パブリッシャーからの挿入がサブスクライバーで適用できませんでした。<br /><br /> **7** = アップロードの削除に失敗: サブスクライバーでの削除がパブリッシャーにアップロードできませんでした。<br /><br /> **8** = 削除のダウンロードに失敗: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = アップロードの更新に失敗: サブスクライバーでの更新がパブリッシャーで適用できませんでした。<br /><br /> **10** = 更新のダウンロードに失敗: パブリッシャーでの更新をサブスクライバーに適用できませんでした。<br /><br /> **11**解像度を =<br /><br /> **12** = 論理レコードの更新が優先削除: 削除された論理レコード競合を避けるがこのテーブルに記録されます。<br /><br /> **13** = 論理レコード競合挿入更新: 更新プログラムと競合して論理レコードを挿入します。<br /><br /> **14** = 論理レコードの削除が優先更新の競合: 競合を避ける論理レコードの更新がこのテーブルに記録されます。|  
|**reason_code**|**int**|状況依存のエラー コード。 この列で使用される値では、更新-更新と更新、削除の競合の場合と同じ、 **conflict_type**します。 ただし、変更の失敗による競合の場合は、マージ エージェントが変更を適用できなかったことを示すエラーが理由コードとなります。 たとえば、マージ エージェントは、主キー違反のため、サブスクライバーで挿入を適用することはできない場合、ログに記録、 **conflict_type** 6 (「挿入のダウンロードに失敗しました」) の**reason_code** 2672 がある、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]主キー違反の内部エラー メッセージ:"%ls 制約の違反 ' %. * ls'。 オブジェクトが重複するキーを挿入できません ' % です。\*ls'"。|  
|**reason_text**|**nvarchar(720)**|状況依存エラーの説明。|  
|**pubid**|**uniqueidentifier**|パブリケーションの識別子です。|  
|**MSrepl_create_time**|**datetime**|競合が発生した時刻です。|  
|**origin_datasource_id**|**uniqueidentifier**|競合している変更が発生したデータベースの識別子です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
