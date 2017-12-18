---
title: "catalog.add_execution_worker (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5ecc54863b47ef55269a068353cbc25bbd5d008
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

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

## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
 
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
 
- ユーザーに適切な権限がない。

- 実行識別子が有効ではない。

- worker エージェント ID が正しくない。

- Scale Out に実行がない。

## <a name="see-also"></a>参照
[Scale Out でのパッケージの実行](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md)。

