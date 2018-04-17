---
title: sp_helpmergepartition (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95cf9955591a1c36ce294e8d7448b296a3399230
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したマージ パブリケーションのパーティション情報を返します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@suser_sname=** ] **'***suser_sname***'**  
 パーティションの定義に使用する SUSER_SNAME 値を指定します。 *suser_sname*は**sysname**既定値は NULL です。 このパラメーターを指定して、結果セットを、SUSER_SNAME が指定された値を解決するパーティションのみに制限します。  
  
> [!NOTE]  
>  ときに*suser_sname*が指定されている*host_name* NULL にする必要があります  
  
 [  **@host_name=** ] **'***host_name***'**  
 パーティションの定義に使用する HOST_NAME 値を指定します。 *host_name*は**sysname**既定値は NULL です。 このパラメーターを指定して、結果セットを、HOST_NAME が指定された値を解決するパーティションのみに制限します。  
  
> [!NOTE]  
>  ときに*suser_sname*が指定されている*host_name* NULL にする必要があります  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パーティション**|**int**|サブスクライバーのパーティションを指定します。|  
|**host_name**|**sysname**|値によってフィルター選択は、サブスクリプションのパーティションを作成するときに使用される値、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)サブスクライバーでの関数。|  
|**suser_sname**|**sysname**|値によってフィルター選択は、サブスクリプションのパーティションを作成するときに使用される値、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)サブスクライバーでの関数。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|サブスクライバーのパーティションの、フィルター選択されたデータ スナップショットの場所です。|  
|**date_refreshed**|**datetime**|前回スナップショット ジョブが実行され、パーティションのフィルター選択されたデータ スナップショットが生成された日付です。|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|パーティションのフィルター選択されたデータ スナップショットを作成するジョブを識別します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergepartition**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergepartition**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergepartition &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
