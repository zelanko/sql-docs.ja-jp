---
title: "集計のデザイン (Analysis Services - 多次元) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7fef45841f28152dfed66aa95f670e8a21a3d903
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="designing-aggregations-analysis-services---multidimensional"></a>集計のデザイン (Analysis Services - 多次元)
  集計とは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で高速なクエリ応答を実現するために、キューブ データを事前に計算してまとめたものです。  
  
 パーティションのストレージ オプションを設定し、集計をデザインするには、集計のデザイン ウィザードを使用します。 このウィザードでは、メジャー グループのパーティションが一度に 1 つずつ処理されるため、パーティションごとに異なるオプションとデザインを選択できます。 画面に表示される手順に従って操作するだけで、パーティションのストレージを構成し、集計をデザインできます。 ストレージの構成の詳細については、「」を参照してください。  
  
 ウィザードでデザインする集計数の制御方法を選択すると、集計がデザインされます。  
  
 その目的は、最適な数の集計をデザインすることにあります。 集計数が最適であれば、満足のゆく応答時間が得られるだけでなく、パーティションのサイズが過度に大きくなるのを防ぐことができます。 集計の数を多くすると、応答時間は短くなりますが、必要な記憶領域が増加し、計算にかかる時間が長くなる場合があります。 さらに、ウィザードでは、初めのころに行う集計の方が、後から行う集計よりもパフォーマンスがより向上するように、さらに多くの集計をデザインしていきます。 不要な集計を減らしても、パフォーマンスを向上させることができます。 ウィザードがデザインする集計の数は、ウィザードに用意されている以下のいずれかの方法で調整できます。  
  
-   集計に使用する記憶領域を制限する。  
  
-   パフォーマンスを制限する。  
  
-   パフォーマンスとサイズの比較を示すグラフが許容可能なパフォーマンスの値で横ばいになったら、ウィザードを手動で停止する。  
  
-   集計をデザインしない。  
  
 ストレージをデザインするには、ウィザードが対象サーバー上の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に接続できる必要があります。 対象サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が実行されていない場合や、それ以外の理由でストレージ デザイン プロセスが対象サーバーに接続できない場合は、ウィザードにエラー メッセージが表示されます。  
  
 ストレージ デザイン ウィザードの最後の手順では、処理を今すぐに行うか、後で行うかを指定するオプションが表示されます。 すぐに処理すると、このウィザードでデザインした集計が作成されますが、保留にすると、デザインした集計は後で処理するために保存され、処理しないでデザイン行動を継続できます。 パーティションのサイズによっては、処理にかなりの時間がかかる場合があります。 必要に応じて、パーティションの処理を中断することもできます。  
  
## <a name="see-also"></a>参照  
 [集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  

