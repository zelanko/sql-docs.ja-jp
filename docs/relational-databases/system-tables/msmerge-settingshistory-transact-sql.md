---
title: MSmerge_settingshistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c35438b1b6df4b2df3ae1af25cb9479f676d9ee5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782920"
---
# <a name="msmergesettingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_settingshistory**テーブルはマージ レプリケーション トポロジに加えられた変更ごとに 1 行で、マージ レプリケーションのアーティクルおよびパブリケーションのプロパティに加えられた変更の履歴を維持するために使用します。 このテーブルには、プロパティの初期設定が行われたときの情報も格納されています。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**eventtime**|**datetime**|イベントが発生した日時。|  
|**pubid**|**uniqueidentifier**|指定したパブリケーションの一意な識別番号。|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**イベントの種類**|**tinyint**|記録するイベントの種類を指定します。以下のいずれかの値をとります。<br /><br /> **1** – の初期パブリケーション レベルのプロパティの設定。<br /><br /> **2** -パブリケーションのプロパティを変更します。<br /><br /> **101** -最初のアーティクルのプロパティの設定。<br /><br /> **102** -アーティクルのプロパティを変更します。|  
|**propertyname**|**sysname**|設定または変更されたプロパティの名前。|  
|**previousvalue**|**sysname**|前のプロパティ値 (プロパティが変更された場合)。|  
|**newvalue**|**sysname**|変更後または作成時のプロパティの値。|  
|**eventtext**|**nvarchar(2000)**|イベントを説明する文字列。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
