---
title: catalog.add_execution_worker (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: dbf3db6560e4a32969abd5162479cb41ca6c40e9
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35409114"
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker を Scale Out 内の実行のインスタンスに追加します。

## <a name="syntax"></a>構文

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>引数
[ @execution_id = ] *execution_id*  
 実行のインスタンスの一意の識別子。 *execution_id* は **bigint** です。  
 
[@workeragent_id = ] *workeragent_id*  
Scale Out Worker の worker エージェント ID。 *workeragent_id* は **uniqueIdentifier** です。

## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
 
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
 
- ユーザーに適切なアクセス許可がない。

- 実行識別子が有効ではない。

- worker エージェント ID が正しくない。

- Scale Out に実行がない。

## <a name="see-also"></a>参照
[Scale Out でのパッケージの実行](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md)。

