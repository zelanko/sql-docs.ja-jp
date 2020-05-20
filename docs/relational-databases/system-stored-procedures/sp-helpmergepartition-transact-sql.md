---
title: sp_helpmergepartition (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 24edec99d34843e15c8cd89c0d7cd123c5e401dd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82818093"
---
# <a name="sp_helpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したマージ パブリケーションのパーティション情報を返します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @suser_sname = ] 'suser_sname'`パーティションを定義するために使用される SUSER_SNAME 値を指定します。 *suser_sname*は**sysname**で、既定値は NULL です。 このパラメーターを指定して、結果セットを、SUSER_SNAME が指定された値を解決するパーティションのみに制限します。  
  
> [!NOTE]  
>  *Suser_sname*を指定する場合は、 *host_name*を NULL にする必要があります。  
  
`[ @host_name = ] 'host_name'`パーティションを定義するために使用される HOST_NAME 値を指定します。 *host_name*は**sysname**で、既定値は NULL です。 このパラメーターを指定して、結果セットを、HOST_NAME が指定された値を解決するパーティションのみに制限します。  
  
> [!NOTE]  
>  *Suser_sname*を指定する場合は、 *host_name*を NULL にする必要があります。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition**|**int**|サブスクライバーパーティションを識別します。|  
|**host_name**|**sysname**|サブスクライバー側の[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)関数の値によってフィルター処理されるサブスクリプションのパーティションを作成するときに使用される値です。|  
|**suser_sname**|**sysname**|サブスクライバー側の[SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)関数の値によってフィルター処理されるサブスクリプションのパーティションを作成するときに使用される値です。|  
|**dynamic_snapshot_location**|**nvarchar(255)**|サブスクライバーのパーティションに対してフィルター選択されたデータスナップショットの場所です。|  
|**date_refreshed**|**datetime**|前回スナップショット ジョブが実行され、パーティションのフィルター選択されたデータ スナップショットが生成された日付です。|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|パーティションのフィルター選択されたデータスナップショットを作成するジョブを識別します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergepartition**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helpmergepartition**を実行できるのは、 **sysadmin**固定サーバーロールおよび**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_addmergepartition &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
