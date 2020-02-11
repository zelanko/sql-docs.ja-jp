---
title: MSmerge_settingshistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: d8cb78229ea20d5b4c1b01b17c9fef1d85ca83b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106322"
---
# <a name="msmerge_settingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_settingshistory**テーブルは、マージレプリケーションのアーティクルおよびパブリケーションのプロパティに加えられた変更の履歴を保持するために使用され、マージレプリケーショントポロジに対して行われた変更ごとに1行のデータを保持します。 このテーブルには、プロパティの初期設定が行われたタイミングに関する情報も格納されます。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**eventtime**|**DATETIME**|イベントが発生した日時。|  
|**pubid**|**UNIQUEIDENTIFIER**|指定されたパブリケーションの一意の id 番号です。|  
|**artid**|**UNIQUEIDENTIFIER**|指定されたアーティクルの一意の識別番号。|  
|**eventtype**|**tinyint**|記録されるイベントの種類を指定します。次のいずれかを指定できます。<br /><br /> **1** -パブリケーションレベルのプロパティの初期設定。<br /><br /> **2** -パブリケーションのプロパティを変更します。<br /><br /> **101** -最初のアーティクルプロパティの設定。<br /><br /> **102** -アーティクルのプロパティを変更します。|  
|**propertyname**|**sysname**|設定または変更されたプロパティの名前|  
|**previousvalue**|**sysname**|プロパティが変更された場合は、前のプロパティ値。|  
|**newvalue**|**sysname**|変更後または作成時のプロパティの値。|  
|**eventtext**|**nvarchar (2000)**|イベントを説明する文字列。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
