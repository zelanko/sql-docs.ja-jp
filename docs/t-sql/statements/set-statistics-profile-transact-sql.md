---
title: "STATISTICS PROFILE (TRANSACT-SQL) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PROFILE
- SET_STATISTICS_PROFILE_TSQL
- PROFILE_TSQL
- SET STATISTICS PROFILE
dev_langs: TSQL
helpviewer_keywords:
- profiles [SQL Server], displaying
- statements [SQL Server], profile information
- SET STATISTICS PROFILE statement
- STATISTICS PROFILE option
- statistical information [SQL Server], profiles
ms.assetid: c635e262-35fa-421a-aa6f-a1c30f351647
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 35de8ba2d942859c9442838813c98fa34fa5419a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-statistics-profile-transact-sql"></a>SET STATISTICS PROFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ステートメントのプロファイル情報を表示します。 STATISTICS PROFILE は、アドホック クエリ、ビュー、ストアド プロシージャに対して機能します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET STATISTICS PROFILE { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 STATISTICS PROFILE が ON の場合、クエリを実行すると、それぞれ通常の結果セットに加えて、クエリ実行のプロファイルを示す追加の結果セットが返されます。  
  
 追加の結果セットには、クエリに関する SHOWPLAN_ALL 列と次の追加列が含まれます。  
  
|列名|Description|  
|-----------------|-----------------|  
|**行数**|それぞれの演算子によって作成された実際の行数|  
|**実行します。**|演算子が実行された回数|  
  
## <a name="permissions"></a>Permissions  
 SET STATISTICS PROFILE を使用して出力を表示するには、次の権限が必要です。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行するための適切な権限。  
  
-   によって参照されているオブジェクトを含むすべてのデータベースでの SHOWPLAN 権限、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]統計プロファイルを生成しないステートメントの結果セットを実行する適切な権限のみ、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが必要です。 STATISTICS PROFILE の結果セットを生成する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの場合は、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行する権限と、SHOWPLAN の権限の両方を持っていることを確認してください。これらの 2 つの権限がないと、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの実行は中断され、プラン表示に関する情報は生成されません。  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [STATISTICS TIME &#40; を設定します。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statistics-time-transact-sql.md)   
 [SET STATISTICS IO &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statistics-io-transact-sql.md)  
  
  
