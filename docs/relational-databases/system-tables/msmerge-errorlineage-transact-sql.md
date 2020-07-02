---
title: MSmerge_errorlineage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1dc2fa3c04c01588b587be3014029202912ddf2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736755"
---
# <a name="msmerge_errorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSmerge_errorlineage**テーブルには、サブスクライバーで削除された行が含まれていますが、その削除はパブリッシャーに反映されていません。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|マージレプリケーション用にパブリッシュされたテーブルに割り当てられた整数値。 **Sysmergearticles**テーブルの [ニックネーム] フィールドに対応します。|  
|**rowguid**|**uniqueidentifier**|行識別子。|  
|**継承**|**varbinary (501)**|行の更新を行ったサブスクライバーとパブリッシャーの履歴リストを格納します。 競合の状況を検出して解決するために使用されます。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
