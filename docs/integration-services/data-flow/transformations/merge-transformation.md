---
title: "マージ変換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0e9bb9533459c720bae5b12d5f4ebdce1f85fc4d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="merge-transformation"></a>マージ変換
  マージ変換は、並べ替えられた 2 つのデータセットを 1 つのデータセットに結合します。 各データセットの行は、各キー列の値に基づいて出力に挿入されます。  
  
 データ フローにマージ変換を含めると、次のタスクを実行できます。  
  
-   テーブルやファイルなど、2 つのデータ ソースのデータをマージします。  
  
-   マージ変換を入れ子にして、複合データセットを作成します。  
  
-   データのエラーを修正後、行を再マージします。  
  
 マージ変換は、全体結合変換と似ています。 次の場合には、マージ変換ではなく全体結合変換を使用します。  
  
-   変換入力の並べ替えを行わない場合。  
  
-   結合された出力を並べ替える必要がない場合。  
  
-   マージ変換は 3 つ以上の入力をとります。  
  
## <a name="input-requirements"></a>入力要件  
 マージ変換では、入力データが並べ替えられている必要があります。 この重要な要件の詳細については、「 [マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。  
  
 マージ変換では、入力されたマージ列のメタデータが一致している必要もあります。 たとえば、数値データ型の列と文字データ型の列はマージできません。 データが文字列データ型の場合、2 番目の入力の列の長さは、マージ先の最初の入力の列の長さ以下である必要があります。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーのマージ変換のユーザー インターフェイスでは、同じメタデータを持つ列は自動的にマップされます。 互換性のあるデータ型を持つ他の列は、手動でマップできます。  
  
 この変換は、2 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## <a name="configuration-of-the-merge-transformation"></a>マージ変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[マージ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [マージ変換エディター](../../../integration-services/data-flow/transformations/merge-transformation-editor.md)」を参照してください。  
  
 プログラムによって設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>関連タスク  
 プロパティの設定方法の詳細については、次の各トピックを参照してください。  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>参照  
 [マージ結合変換](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Union All Transformation](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
