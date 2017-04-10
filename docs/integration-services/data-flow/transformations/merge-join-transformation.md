---
title: "マージ結合変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.mergejointrans.f1"
helpviewer_keywords: 
  - "データセット [Integration Services]"
  - "マージ結合変換"
  - "データセット [Integration Services], 結合"
  - "データセットの結合 [Integration Services]"
  - "結合 [SQL Server], SSIS"
ms.assetid: cd8b0412-f83b-4bd2-b227-e53dcfd941a8
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# マージ結合変換
  マージ結合変換では、FULL、LEFT、または INNER 結合を使用して並べ替えた 2 つのデータセットを結合した出力が生成されます。 たとえば、LEFT 結合を使用して、製品情報を含むテーブルを、製品が製造された国または地域を一覧表示するテーブルと結合します。 その結果、すべての製品とその製造元である国または地域を一覧表示するテーブルが生成されます。  
  
 マージ結合変換は、次の方法で構成できます。  
  
-   FULL、LEFT、または INNER 結合のうち、どの結合を使用するかを指定します。  
  
-   結合で使用する列を指定します。  
  
-   NULL 値を、他の NULL と等しい値として処理するかどうかを指定します。  
  
    > [!NOTE]  
    >  NULL 値どうしを等しい値として扱わない場合、マージ結合変換では、SQL Server データベース エンジンによる処理方法と同様に NULL 値が処理されます。  
  
 この変換は、2 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## 入力要件  
 マージ結合変換では、入力データが並べ替えられている必要があります。 この重要な要件の詳細については、「[マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。  
  
## 結合要件  
 マージ結合変換では、結合列のメタデータが一致している必要があります。 たとえば、数値データ型の列と文字データ型の列は結合できません。 データが文字列データ型の場合、2 番目の入力の列の長さは、マージ先の最初の入力の列の長さ以下である必要があります。  
  
## バッファー スロットル  
 マイクロソフトが行った変更により、マージ結合変換によってメモリが過度に消費されるリスクが軽減したため、 **MaxBuffersPerInput** プロパティの値を構成する必要はなくなりました。 この問題は、マージ結合の複数の入力からデータが不均一なレートで生成される場合に発生することがありました。  
  
## 関連タスク  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 この変換のプロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [マージ結合変換を使用してデータセットを拡張する](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## 参照  
 [マージ結合変換エディター](../../../integration-services/data-flow/transformations/merge-join-transformation-editor.md)   
 [マージ変換](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [全体結合変換](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  