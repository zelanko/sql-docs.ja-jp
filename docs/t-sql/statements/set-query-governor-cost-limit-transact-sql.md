---
title: SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT
- SET_QUERY_GOVERNOR_COST_LIMIT_TSQL
- QUERY_GOVERNOR_COST_LIMIT
- QUERY_GOVERNOR_COST_LIMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT statement
- connections [SQL Server], overriding
- QUERY_GOVERNOR_COST_LIMIT option
- overriding connection values
ms.assetid: 3424bb44-6915-462d-a8d7-fe834af81387
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a96642c6a0dd50ccb8717e84a6defec516196d87
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="set-querygovernorcostlimit-transact-sql"></a>SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在構成されているオーバーライド**クエリ ガバナー コスト制限**現在の接続の値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET QUERY_GOVERNOR_COST_LIMIT value  
```  
  
## <a name="arguments"></a>引数  
 *value*  
 クエリの最大実行時間を表す数値または整数値です。 値は、最も近い整数に切り捨てられます。 負の値は 0 に切り上げられます。 クエリ ガバナーは、見積コストがこの値を超えるクエリの実行を許可しません。 クエリ ガバナーは、オフには、このオプションを 0 (既定値) を指定して、無期限に実行するすべてのクエリが許可されます。  
  
 "クエリ コスト" とは、特定のハードウェア構成でクエリを完了するために必要とされる予測所要時間を秒単位で表したものです。  
  
## <a name="remarks"></a>解説  
 SET QUERY_GOVERNOR_COST_LIMIT の設定は現在の接続にだけ適用され、現在の接続が終了するまで有効です。 使用して、 [query governor cost limit サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md)オプション**sp_configure**を変更、サーバー全体の query governor cost limit の値。 このオプションを構成する方法の詳細については、次を参照してください。 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)と[サーバー構成オプション &#40;です。SQL Server &#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 SET QUERY_GOVERNOR_COST_LIMIT は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
