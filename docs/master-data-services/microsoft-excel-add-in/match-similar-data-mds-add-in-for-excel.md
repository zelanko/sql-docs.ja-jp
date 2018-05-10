---
title: 類似データの結合 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 86a1397a0cfaac0aaef4c271f5dbd89a1d0311c9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>類似データの照合 (Excel 用 MDS アドイン)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、Data Quality Services (DQS) 機能を使用してデータ内の類似性を見つけます。  
  
 この手順を実行するには、次のどちらかの操作を実行します。  
  
-   既定の Data Quality Services ナレッジ ベースを使用します。  
  
-   独自のカスタムな DQS ナレッジ ベースと照合ポリシーを作成します。 詳細については、「 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)」をご参照ください。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   MDS によって管理されるデータが含まれているワークシートが必要です。 詳細については、「 [マスター データ サービスからデータを Excel にエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)」を参照してください。  
  
-   省略可。 類似性をチェックする前に、MDS によって管理されるデータとその他のデータを結合することができます。 詳細については、「 [データの結合 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md)」を参照してください。  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>既定のナレッジ ベースを使用して類似性を見つけるには  
  
1.  MDS によって管理されるデータを含むワークシートで、 **[データ品質]** グループの **[データの照合]** をクリックします。  
  
2.  **[データの照合]** ダイアログ ボックスで、 **[DQS 知識ベース]** の一覧から **[DQS データ (既定値)]** を選択します。  
  
3.  照合するデータを含む各列について、ダイアログ ボックスで行を追加します。 このダイアログ ボックスのフィールドの詳細については、「 [照合ルールのパラメーターを設定する方法](../../data-quality-services/create-a-matching-policy.md#MatchingRules)」を参照してください。  
  
4.  すべての重み値の合計が 100% になったら、 **[OK]** をクリックします。  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>カスタム ナレッジ ベースを使用して類似性を見つけるには  
  
1.  MDS によって管理されるデータを含むワークシートで、 **[データ品質]** グループの **[データの照合]** をクリックします。  
  
2.  **[DQS 知識ベース]** の一覧から、カスタム ナレッジ ベースの名前を選択します。  
  
3.  ワークシート内の各列について、DQS ドメインを選択します。  
  
4.  すべての DQS ドメインがワークシート内の列にマップされたら、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>Next Steps  
  
-   類似するデータを判別するには、追加情報を表示します。 詳細については、「[データ品質照合の列 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/data-quality-matching-columns-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Excel 用 MDS アドインでのデータ品質照合](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [データ照合](../../data-quality-services/data-matching.md)  
  
  
