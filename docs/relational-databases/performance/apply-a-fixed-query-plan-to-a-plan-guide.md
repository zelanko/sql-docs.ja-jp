---
title: プラン ガイドへの固定クエリ プランの適用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6111613cb6fe4aeed55dda5e736d2c68b2da487
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>プラン ガイドへの固定クエリ プランの適用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  OBJECT 型または SQL 型のプラン ガイドには固定クエリ プランを適用できます。 特定のクエリに対してオプティマイザーによって選択された実行プランよりもパフォーマンスの高い既存の実行プランがわかっている場合は、固定クエリ プランを適用するプラン ガイドを使用すると便利です。  
  
 次の例では、単純なアドホック SQL ステートメントのプラン ガイドを作成します。 このステートメントの目的のクエリ プランは、クエリの XML プラン表示を `@hints` パラメーターで直接指定することにより、プラン ガイドで提供されます。 最初に SQL ステートメントを実行して、プラン キャッシュ内にプランを生成します。 この例では、生成されたプランが目的のプランであり、追加のクエリ チューニングが不要であると想定しています。 クエリの XML プラン表示は、 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`、および `sys.dm_exec_text_query_plan` の各動的管理ビューをクエリすることにより取得され、 `@xml_showplan` 変数に割り当てられます。 次に `@xml_showplan` 変数が、 `sp_create_plan_guide` パラメーターで `@hints` ステートメントに渡されます。 または、 [sp_create_plan_guide_from_handle](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md) ストアド プロシージャを使用して、プラン キャッシュ内のクエリ プランからプラン ガイドを作成することもできます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
