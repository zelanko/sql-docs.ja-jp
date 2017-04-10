---
title: "DQS クレンジング変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ修正"
  - "データの修正"
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# DQS クレンジング変換
  DQS クレンジング変換では、Data Quality Services (DQS) を使用して、接続されたデータ ソースまたは類似のデータ ソース用に作成された承認済みのルールを適用することにより、接続されたデータ ソースのデータを修正します。 データ修正ルールの詳細については、「 [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。 DQS の詳細については、「 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。  
  
 データを修正する必要があるかどうかを判断するために、DQS クレンジング変換は、次の条件が当てはまる場合に、入力列のデータを処理します。  
  
-   データ修正のために列が選択されている。  
  
-   列のデータ型でデータ修正がサポートされている。  
  
-   列が、互換性のあるデータ型のドメインにマップされている。  
  
 また、変換には、低レベルのエラーを処理するように構成するエラー出力も含まれます。 エラー出力を構成するには、 **DQS クレンジング変換エディター**を使用します。  
  
 [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) をデータ フローに含めて、重複部分と考えられるデータ行を特定することができます。  
  
## データ品質プロジェクトと値  
 DQS クレンジング変換によってデータを処理すると、クレンジング プロジェクトが Data Quality Server に作成されます。 データ品質クライアントを使用してプロジェクトを管理します。 また、データ品質クライアントを使用して、プロジェクトの値を DQS のナレッジ ベースのドメインにインポートできます。 値は、DQS クレンジング変換で使用するように構成されているドメイン (またはリンク ドメイン) にしかインポートできません。  
  
## 関連タスク  
  
-   [Data Quality Client で Integration Services プロジェクトを開く](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Import Cleansing Project Values into a Domain](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [データ ソースにデータ品質ルールを適用する](../../../integration-services/data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
## 関連コンテンツ  
  
-   [データ品質プロジェクトを開く、ロックを解除する、名前を変更する、削除する](https://msdn.microsoft.com/library/hh510417.aspx)  
  
-   social.technet.microsoft.com の記事「 [複合ドメインを使用した複雑なデータのクレンジング](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)」  
  
  