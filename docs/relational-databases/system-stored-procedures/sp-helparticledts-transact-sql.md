---
title: sp_helparticledts (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords:
- sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b5355ea4993944a4a47b59eb2cad0565e0c396c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82815825"
---
# <a name="sp_helparticledts-transact-sql"></a>sp_helparticledts (Transact-sql)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Visual Basic を使用して変換サブスクリプションを作成するときに使用する、正しいカスタムタスク名に関する情報を取得するために使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @article = ] 'article'`パブリケーション内のアーティクルの名前を指定します。 *アーティクル*は**sysname**で、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**sysname**|スナップショットデータがコピーされる前に発生するプログラミングタスクのタスク名。 スクリプト エラーが発生しても、プログラムはそのまま実行されます。|  
|**pre_script_task_name**|**sysname**|スナップショットデータがコピーされる前に発生するプログラミングタスクのタスク名。 プログラムの実行はエラー発生時に停止します。|  
|**transformation_task_name**|**sysname**|データドリブンクエリタスクを使用するときのプログラミングタスクのタスク名。|  
|**post_script_ignore_error_task_name**|**sysname**|スナップショット データをコピーした後に発生するプログラミング タスクのタスク名。 スクリプト エラーが発生しても、プログラムはそのまま実行されます。|  
|**post_script_task_name**|**sysname**|スナップショット データをコピーした後に発生するプログラミング タスクのタスク名。 プログラムの実行はエラー発生時に停止します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_helparticledts**は、スナップショットレプリケーションおよびトランザクションレプリケーションで使用します。  
  
 レプリケーション データ変換サービス (DTS) プログラム内のタスクに名前を付ける場合は、レプリケーション エージェントで要求される名前付け規則に従う必要があります。 SQL 実行タスクなどのカスタムタスクの場合、名前は、アーティクル名、プレフィックス、および省略可能な部分で構成される連結文字列になります。 コードを記述するときに、タスク名がわからない場合、結果セットには使用する必要があるタスク名が示されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helparticledts**を実行できるのは、 **sysadmin**固定サーバーロールおよび**db_owner**固定データベースロールのメンバーだけです。  
  
  
