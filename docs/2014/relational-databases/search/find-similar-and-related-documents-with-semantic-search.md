---
title: セマンティック検索による類似および関連したドキュメントの取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b2e30534fb5e0232ff2046e30e2e14075dfb807
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011317"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>セマンティック検索による類似および関連したドキュメントの取得
  統計的セマンティック インデックス作成用に構成されている列での、類似性または関連性のあるドキュメントやテキスト値の検索方法と、どのように類似または関連しているかという情報の検索方法について説明します。  
  
##  <a name="BasicsQuerySimilar"></a>類似または関連するドキュメントの検索  
  
###  <a name="HowToQuerySimilar"></a>方法: SEMANTICSIMILARITYTABLE を使用して類似または関連するドキュメントを検索する  
 特定の列で類似または関連したドキュメントを識別するには、[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 関数を使用してクエリを実行します。  
  
 **SEMANTICSIMILARITYTABLE**は、0行、1行、または複数の行から成るテーブルを返します。指定された列の内容は、指定されたドキュメントと意味的に似ています。 この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。  
  
 複数の列にわたって類似したドキュメントに対するクエリを実行することはできません。 
  **SEMANTICSIMILARITYTABLE** 関数は、 **source_key** 引数によって識別されるソース列と同じ列からのみ結果を取得します。  
  
 
  **SEMANTICSIMILARITYTABLE** 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、「[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)」を参照してください。  
  
> [!IMPORTANT]  
>  対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。  
  
###  <a name="HowToIdentifySimilar"></a>例: 別のドキュメントに類似している上位のドキュメントを検索する  
 次の例では、AdventureWorks2012 サンプルデータベースの Humanresources.employee テーブルから、によっ*@CandidateID*て指定された候補に類似する上位10の候補を取得します。  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="BasicsQuerySimilarity"></a>ドキュメントが類似または関連しているかどうかに関する情報の検索  
  
###  <a name="HowToQuerySimilarity"></a>方法: ドキュメントが類似しているか、SEMANTICSIMILARITYDETAILSTABLE と関連付けられているかに関する情報を検索する  
 ドキュメントが類似または関連する原因となっているキー フレーズに関する情報を表示するには、[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 関数を使用してクエリを実行します。  
  
 **SEMANTICSIMILARITYDETAILSTABLE**は、意味が似たコンテンツを持つ2つのドキュメント (ソースドキュメントと一致するドキュメント) に共通するキーフレーズの0行、1行、または複数の行から成るテーブルを返します。 この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。  
  
 
  **SEMANTICSIMILARITYDETAILTABLE** 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、「[semanticsimilaritydetailtable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)」を参照してください。  
  
> [!IMPORTANT]  
>  対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。  
  
###  <a name="HowToSimilarPhrases"></a>例: ドキュメント間で類似している上位のキーフレーズを検索する  
 次の例では、AdventureWorks2012 サンプル データベースの **HumanResources.JobCandidate** テーブル内の指定された候補間で最も類似スコアが高い 5 つのキー フレーズを取得します。  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
