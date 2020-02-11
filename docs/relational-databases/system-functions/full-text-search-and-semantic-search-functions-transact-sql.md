---
title: フルテキスト検索およびセマンティック検索関数 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58bf5650a5ab06783ad0c889bc3286184a7d73ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042756"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>フルテキスト検索およびセマンティック検索関数 (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、フルテキスト検索とセマンティック検索に関係するシステム関数について説明します。  
  
## <a name="full-text-search-functions"></a>フルテキスト検索関数  
 [CONTAINSTABLE &#40;Transact-sql&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 1つの単語と語句の完全一致またはあいまい一致を含む列、特定の範囲内での近接語句、または重み付け一致を含む列について、0行、1行、または複数の行から成るテーブルを返します。  
  
 [FREETEXTTABLE &#40;Transact-sql&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 指定された*freetext_string*内のテキストの正確な表現だけでなく、意味に一致する値を含む列について、0行、1行、または複数の行から成るテーブルを返します。  
  
## <a name="semantic-search-functions"></a>セマンティック検索関数  
 [semantickeyphrasetable &#40;Transact-sql&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 指定されたテーブル内の列に関連付けられているキーフレーズに対して、0行、1行、または複数の行を含むテーブルを返します。  
  
 [semanticsimilaritydetailstable &#40;Transact-sql&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 2つのドキュメント (ソースドキュメントと一致するドキュメント) に共通し、意味が似ているキーフレーズの0行、1行、または複数の行から成るテーブルを返します。  
  
 [semanticsimilaritytable &#40;Transact-sql&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 指定されたドキュメントに意味が似ているコンテンツを持つこれらの列に対し、0 行、1 行、または複数の行から成るテーブルを返します。  
  
  
