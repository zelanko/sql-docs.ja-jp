---
title: sp_showrowreplicainfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9b56608d6ba26760a0a6da5e841f6ce38848774
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028181"
---
# <a name="spshowrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ レプリケーション内のアーティクルとして使用されているテーブル内の行に関する情報を表示します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@ownername**=] **'***ownername***'**  
 テーブルの所有者の名前です。 *ownername*は**sysname**、既定値は NULL です。 このパラメーターは、データベースに、テーブル名は同じだがテーブル所有者がそれぞれ異なる複数のテーブルが含まれる場合、テーブルを区別するのに効果的です。  
  
 [  **@tablename =**] **'***tablename***'**  
 情報を返す行を含むテーブルの名前を指定します。 *tablename*は**sysname**、既定値は NULL です。  
  
 [  **@rowguid =**] *rowguid*  
 行の一意識別子です。 *rowguid*は**uniqueidentifier**、既定値はありません。  
  
 [ **@show**=] **'***表示***'**  
 結果セットに返す情報量を指定します。 *表示*は**nvarchar (20)** 両方の既定値。 場合**行**行のバージョン情報のみが返されます。 場合**列**列のバージョン情報のみが返されます。 場合**両方**、両方の行および列情報が返されます。  
  
## <a name="result-sets-for-row-information"></a>行情報の結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|行バージョン エントリを作成したデータベースを処理するサーバーの名前です。|  
|**db_name**|**sysname**|このエントリを作成したデータベースの名前です。|  
|**db_nickname**|**binary(6)**|このエントリを作成したデータベースのニックネームです。|  
|**version**|**int**|エントリのバージョンです。|  
|**current_state**|**nvarchar (9)**|行の現在の状態に関する情報を返します。<br /><br /> **y** -行データが行の現在の状態を表します。<br /><br /> **n** -行データは、行の現在の状態を表しません。<br /><br /> **\<該当なし >** は適用されません。<br /><br /> **\<不明な >** -現在の状態を特定できません。|  
|**rowversion_table**|**nchar(17)**|格納される行バージョンであるかどうかを示す、 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)テーブルまたは[MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)テーブル。|  
|**comment**|**nvarchar (255)**|この行バージョン エントリに関する追加情報です。 通常、このフィールドは空です。|  
  
## <a name="result-sets-for-column-information"></a>列情報の結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|列バージョン エントリを作成したデータベースを処理するサーバーの名前です。|  
|**db_name**|**sysname**|このエントリを作成したデータベースの名前です。|  
|**db_nickname**|**binary(6)**|このエントリを作成したデータベースのニックネームです。|  
|**version**|**int**|エントリのバージョンです。|  
|**colname**|**sysname**|列バージョン エントリに対応するアーティクル列の名前です。|  
|**comment**|**nvarchar (255)**|この列バージョン エントリに関する追加情報です。 通常、このフィールドは空です。|  
  
## <a name="result-set-for-both"></a>両方の結果セット  
 場合、値**両方**に選択されている*表示*行と列の両方の結果セットが返されます。  
  
## <a name="remarks"></a>コメント  
 **sp_showrowreplicainfo**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **sp_showrowreplicainfo**のメンバーによってのみ実行されることができます、 **db_owner**のパブリケーション データベースのパブリケーション アクセス リスト (PAL) のメンバー、またはパブリケーション データベースの固定データベース ロール。  
  
## <a name="see-also"></a>参照  
 [検出およびマージ レプリケーションの競合を解決します。](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
