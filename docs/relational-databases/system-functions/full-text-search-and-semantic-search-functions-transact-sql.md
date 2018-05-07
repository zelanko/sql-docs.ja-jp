---
title: フルテキスト検索およびセマンティック検索関数 (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04356970f56a3a2e5ee8f2a824b722801fe7262a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>フルテキスト検索およびセマンティック検索関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、フルテキスト検索とセマンティック検索に関係するシステム関数について説明します。  
  
## <a name="full-text-search-functions"></a>フルテキスト検索関数  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 単語または語句との完全一致検索やあいまい一致検索、特定の範囲内での近接検索、または重み付き検索を行う列に対して、0 行、1 行、または複数の行から成るテーブルを返します。  
  
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 0、1、または複数の行を意味と、正確な表現だけでなく、指定したテキストの一致する値を格納している列のテーブルを返します*freetext_string*です。  
  
## <a name="semantic-search-functions"></a>セマンティック検索関数  
 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 指定されたテーブル内の列に関連付けられているこれらのキー フレーズに対し、0 行、1 行、または複数の行を含むテーブルを返します。  
  
 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 2 つのドキュメント (ソース ドキュメントと一致するドキュメント) コンテンツを持つ意味が似て、一般的な 0、1、またはキー フレーズの複数の行のテーブルを返します。  
  
 [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 指定されたドキュメントに意味が似ているコンテンツを持つこれらの列に対し、0 行、1 行、または複数の行から成るテーブルを返します。  
  
  
