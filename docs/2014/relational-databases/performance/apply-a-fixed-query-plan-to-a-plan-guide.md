---
title: プラン ガイドへの固定クエリ プランの適用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066065"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>プラン ガイドへの固定クエリ プランの適用
  OBJECT 型または SQL 型のプラン ガイドには固定クエリ プランを適用できます。 特定のクエリに対してオプティマイザーによって選択された実行プランよりもパフォーマンスの高い既存の実行プランがわかっている場合は、固定クエリ プランを適用するプラン ガイドを使用すると便利です。  
  
 次の例では、単純なアドホック SQL ステートメントのプラン ガイドを作成します。 このステートメントの目的のクエリ プランは、クエリの XML プラン表示を `@hints` パラメーターで直接指定することにより、プラン ガイドで提供されます。 最初に SQL ステートメントを実行して、プラン キャッシュ内にプランを生成します。 この例では、生成されたプランが目的のプランであり、追加のクエリ チューニングが不要であると想定しています。 クエリの XML プラン表示は、 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`、および `sys.dm_exec_text_query_plan` の各動的管理ビューをクエリすることにより取得され、 `@xml_showplan` 変数に割り当てられます。 次に `@xml_showplan` 変数が、 `sp_create_plan_guide` パラメーターで `@hints` ステートメントに渡されます。 または、 [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) ストアド プロシージャを使用して、プラン キャッシュ内のクエリ プランからプラン ガイドを作成することもできます。  
  
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
  
  
