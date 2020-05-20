---
title: sp_showrowreplicainfo (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 34fa326c5982ee36cf0ee00fb66c8bac1714c06a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830948"
---
# <a name="sp_showrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージレプリケーションのアーティクルとして使用されているテーブル内の行に関する情報を表示します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @ownername = ] 'ownername'`テーブル所有者の名前を指定します。 *ownername*は**sysname**,、既定値は NULL です。 このパラメーターは、データベースに同じ名前の複数のテーブルが含まれていて、各テーブルの所有者が異なる場合に、テーブルを区別するのに役立ちます。  
  
`[ @tablename = ] 'tablename'`情報が返される行を含むテーブルの名前を指定します。 *tablename*は**sysname**,、既定値は NULL です。  
  
`[ @rowguid = ] rowguid`行の一意の識別子を示します。 *rowguid*は**uniqueidentifier**,、既定値はありません。  
  
`[ @show = ] 'show'`結果セットに返す情報の量を決定します。 *show*は**nvarchar (20)** で、既定値は BOTH です。 **行**の場合は、行のバージョン情報のみが返されます。 **列**の場合は、列のバージョン情報のみが返されます。 **両方**の場合、行と列の両方の情報が返されます。  
  
## <a name="result-sets-for-row-information"></a>行情報の結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|行バージョンエントリを作成したデータベースをホストしているサーバーの名前。|  
|**db_name**|**sysname**|このエントリを作成したデータベースの名前です。|  
|**db_nickname**|**binary(6)**|このエントリを作成したデータベースのニックネーム。|  
|**version**|**int**|エントリのバージョン。|  
|**current_state**|**nvarchar (9)**|行の現在の状態に関する情報を返します。<br /><br /> **y**行のデータは、行の現在の状態を表します。<br /><br /> **n**行のデータは、行の現在の状態を表していません。<br /><br /> ** \< n/a>** -適用されません。<br /><br /> ** \< 不明な>** -現在の状態を特定できません。|  
|**rowversion_table**|**nchar (17)**|行のバージョンが[MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)テーブルと[MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)テーブルのどちらに格納されているかを示します。|  
|**comment**|**nvarchar(255)**|この行バージョンエントリに関する追加情報。 通常、このフィールドは空です。|  
  
## <a name="result-sets-for-column-information"></a>列情報の結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|列バージョン エントリを作成したデータベースを処理するサーバーの名前です。|  
|**db_name**|**sysname**|このエントリを作成したデータベースの名前です。|  
|**db_nickname**|**binary(6)**|このエントリを作成したデータベースのニックネーム。|  
|**version**|**int**|エントリのバージョン。|  
|**colname**|**sysname**|列バージョンエントリが表すアーティクル列の名前。|  
|**comment**|**nvarchar(255)**|この列バージョン エントリに関する追加情報です。 通常、このフィールドは空です。|  
  
## <a name="result-set-for-both"></a>両方の結果セット  
 **両方**の値が*show*に選択されている場合、行と列の両方の結果セットが返されます。  
  
## <a name="remarks"></a>解説  
 **sp_showrowreplicainfo**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **sp_showrowreplicainfo**を実行できるのは、パブリケーションデータベースの**db_owner**固定データベースロールのメンバー、またはパブリケーションデータベースのパブリケーションアクセスリスト (PAL) のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [マージレプリケーションの競合の検出と解決](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
