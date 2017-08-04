---
title: "データ ソースにデータ品質ルールを適用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7db6b5fc01c5d85b75ebdd6c78ba004a94135bf
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="apply-data-quality-rules-to-data-source"></a>データ ソースにデータ品質ルールを適用する
  Data Quality Services (DQS) を使用して、DQS クレンジング変換をデータ ソースに接続することで、パッケージ データ フロー内のデータを修正できます。 DQS の詳細については、「[Data Quality Services の概念](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。 変換の詳細については、「[DQS クレンジング変換](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)」を参照してください。  
  
 DQS クレンジング変換によってデータを処理すると、データ品質プロジェクトが Data Quality Server に作成されます。 データ品質クライアントを使用してプロジェクトを管理します。 詳細については、「 [データ品質プロジェクトを開く、ロックを解除する、名前を変更する、削除する](https://msdn.microsoft.com/library/hh510417.aspx)」を参照してください。  
  
### <a name="to-correct-data-in-the-data-flow"></a>データ フロー内のデータを修正するには  
  
1.  パッケージを作成します。  
  
2.  DQS クレンジング変換を追加し、構成します。 詳細については、「[[DQS クレンジング変換エディター] ダイアログ ボックス](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md)」を参照してください。  
  
3.  データ ソースに DQS クレンジング変換を接続します。  
  
  
