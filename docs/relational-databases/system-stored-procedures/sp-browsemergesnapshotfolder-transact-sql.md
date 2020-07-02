---
title: sp_browsemergesnapshotfolder (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c930347c18dc257b5a6c51d2b013d2429b269fe
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715995"
---
# <a name="sp_browsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  マージパブリケーションに対して生成された最新のスナップショットの完全なパスを返します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar (2000)**|スナップショットディレクトリへの完全パスです。|  
  
## <a name="remarks"></a>Remarks  
 **sp_browsemergesnapshotfolder**は、マージレプリケーションで使用します。  
  
 パブリッシャーの作業ディレクトリとパブリッシャーのスナップショットフォルダーの両方でスナップショットファイルを生成するようにパブリケーションが設定されている場合、結果セットには2つの行が含まれます。最初の行にはパブリケーションスナップショットフォルダーが含まれ、2番目の行にはパブリッシャーの作業ディレクトリが含まれます。  
  
 **sp_browsemergesnapshotfolder**は、マージスナップショットファイルが生成されるディレクトリを特定するのに役立ちます。 このフォルダーおよびパスとその内容をリムーバブル メディアにコピーし、スナップショットを使用してスナップショットの代替位置からサブスクリプションを同期することができます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_browsemergesnapshotfolder**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
