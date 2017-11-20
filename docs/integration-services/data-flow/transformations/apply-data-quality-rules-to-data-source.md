---
title: "データ ソースにデータ品質ルールを適用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: aab3d6859df95dff080fe93aa686ee70b3c5c13a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="apply-data-quality-rules-to-data-source"></a>データ ソースにデータ品質ルールを適用する
  Data Quality Services (DQS) を使用して、DQS クレンジング変換をデータ ソースに接続することで、パッケージ データ フロー内のデータを修正できます。 DQS の詳細については、「 [Data Quality Services の概念](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。 変換の詳細については、「 [DQS クレンジング変換](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)」を参照してください。  
  
 DQS クレンジング変換によってデータを処理すると、データ品質プロジェクトが Data Quality Server に作成されます。 データ品質クライアントを使用してプロジェクトを管理します。 詳細については、「[データ品質プロジェクトを開く、ロックを解除する、名前を変更する、削除する](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md)」を参照してください。  
  
### <a name="to-correct-data-in-the-data-flow"></a>データ フロー内のデータを修正するには  
  
1.  パッケージを作成します。  
  
2.  DQS クレンジング変換を追加し、構成します。 詳細については、「 [[DQS クレンジング変換エディター] ダイアログ ボックス](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md)」を参照してください。  
  
3.  データ ソースに DQS クレンジング変換を接続します。  
  
  

