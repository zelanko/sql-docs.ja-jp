---
title: DQS クレンジング変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cec475debf0c386b51a165df743b2a6893992a49
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178934"
---
# <a name="dqs-cleansing-transformation"></a>DQS クレンジング変換
  DQS クレンジング変換では、Data Quality Services (DQS) を使用して、接続されたデータ ソースまたは類似のデータ ソース用に作成された承認済みのルールを適用することにより、接続されたデータ ソースのデータを修正します。 データ修正ルールの詳細については、「 [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。 DQS の詳細については、「 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。  
  
 データを修正する必要があるかどうかを判断するために、DQS クレンジング変換は、次の条件が当てはまる場合に、入力列のデータを処理します。  
  
-   データ修正のために列が選択されている。  
  
-   列のデータ型でデータ修正がサポートされている。  
  
-   列が、互換性のあるデータ型のドメインにマップされている。  
  
 また、変換には、低レベルのエラーを処理するように構成するエラー出力も含まれます。 エラー出力を構成するには、 **DQS クレンジング変換エディター**を使用します。  
  
 [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) をデータ フローに含めて、重複部分と考えられるデータ行を特定することができます。  
  
## <a name="data-quality-projects-and-values"></a>データ品質プロジェクトと値  
 DQS クレンジング変換によってデータを処理すると、クレンジング プロジェクトが Data Quality Server に作成されます。 データ品質クライアントを使用してプロジェクトを管理します。 また、データ品質クライアントを使用して、プロジェクトの値を DQS のナレッジ ベースのドメインにインポートできます。 値は、DQS クレンジング変換で使用するように構成されているドメイン (またはリンク ドメイン) にしかインポートできません。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Data Quality Client で Integration Services プロジェクトを開く](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Import Cleansing Project Values into a Domain](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [データ ソースにデータ品質ルールを適用する](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [管理&#40;を開く、ロック解除、名前変更、および削除&#41;データ品質プロジェクト](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   social.technet.microsoft.com の記事「 [複合ドメインを使用した複雑なデータのクレンジング](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)」  
  
  