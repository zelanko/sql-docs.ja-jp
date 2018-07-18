---
title: AMO OLAP クラス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: 397509b7-a4fb-40de-aa30-c66dc9ed2105
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1fcf669d63554c9a57dc927cb0071fbc17a9f2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280408"
---
# <a name="amo-olap-classes"></a>AMO OLAP クラス
  分析管理オブジェクト (AMO) OLAP クラスは、キューブやディメンションに加えて、主要業績評価指標 (KPI)、アクション、プロアクティブ キャッシュなどの関連オブジェクトを作成、変更、削除、および処理する際に役立ちます。  
  
 AMO プログラミング環境のセットアップに関する詳細については、どのサーバー、データベースへのアクセスまたはデータの定義との接続を確立するためにソースし、データ ソース ビューを参照してください[AMO 基礎クラス](amo-fundamental-classes.md)します。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [ディメンション オブジェクト](#Dimensions)  
  
-   [キューブ オブジェクト](#Cubes)  
  
-   [MeasureGroup オブジェクト](#MeasureGroups)  
  
-   [Partition オブジェクト](#Partition)  
  
-   [AggregationDesign オブジェクト](#AggregationDesign)  
  
-   [Aggregation オブジェクト](#Aggregation)  
  
-   [Action オブジェクト](#Action)  
  
-   [KPI オブジェクト](#KPI)  
  
-   [Perspective オブジェクト](#Perspective)  
  
-   [Translation オブジェクト](#Translation)  
  
-   [ProactiveCaching オブジェクト](#ProactiveCaching)  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![Amo OLAP クラス](../../../analysis-services/dev-guide/media/amo-olapclasses.gif "amo OLAP クラス")  
  
## <a name="basic-classes"></a>基本クラス  
  
###  <a name="Dimensions"></a> ディメンション オブジェクト  
 ディメンションの作成は、親データベースのディメンション コレクションにこれを追加し、Update メソッドを使用してサーバーに対して <xref:Microsoft.AnalysisServices.Dimension> オブジェクトを更新することにより行われます。  
  
 ディメンションを削除するには、<xref:Microsoft.AnalysisServices.Dimension> の Drop メソッドを使用してこれを削除する必要があります。 Remove メソッドを使用して、データベースのディメンション コレクションから <xref:Microsoft.AnalysisServices.Dimension> を削除した場合、AMO オブジェクト モデル内では削除されますが、サーバー上では削除されません。  
  
 <xref:Microsoft.AnalysisServices.Dimension> オブジェクトは、作成後に処理できます。 <xref:Microsoft.AnalysisServices.Dimension> は、独自の処理メソッドを使用して処理するか、親オブジェクトの処理時に親オブジェクトの処理メソッドを使用して処理することができます。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Dimension>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="Cubes"></a> キューブ オブジェクト  
 キューブを作成するには、データベースのキューブ コレクションに新しいキューブを追加した後、Update メソッドを使用して、サーバー上の <xref:Microsoft.AnalysisServices.Cube> オブジェクトを更新します。 キューブの Update メソッドは、パラメーター UpdateOptions.ExpandFull で、変更された、キューブ内のすべてのオブジェクトは、この更新アクション内のサーバーに更新されますを含めることができます。  
  
 キューブを削除するには、<xref:Microsoft.AnalysisServices.Cube> の Drop メソッドを使用してこれを削除する必要があります。 コレクションからキューブを削除しても、サーバーには影響を与えません。  
  
 <xref:Microsoft.AnalysisServices.Cube> オブジェクトは、作成後に処理できます。 <xref:Microsoft.AnalysisServices.Cube> は、独自の処理メソッドを使用して処理するか、親オブジェクトがそれ自体を独自の Process メソッドを使用して処理する際に処理することができます。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Cube>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="MeasureGroups"></a> MeasureGroup オブジェクト  
 メジャー グループを作成するには、キューブのメジャー グループ コレクションに新しいメジャー グループを追加した後、独自の Update メソッドを使用して、サーバー上の <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトを更新します。 <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトを削除するには、独自の Drop メソッドを使用します。  
  
 <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトは、作成後に処理できます。 <xref:Microsoft.AnalysisServices.MeasureGroup> は、独自の Process メソッドを使用して処理するか、親オブジェクトがそれ自体を独自の Process メソッドで処理する際に処理することができます。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.MeasureGroup>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="Partition"></a> Partition オブジェクト  
 <xref:Microsoft.AnalysisServices.Partition> オブジェクトの作成は、親メジャー グループのパーティション コレクションにこれを追加し、Update メソッドを使用してサーバーに対して <xref:Microsoft.AnalysisServices.Partition> オブジェクトを更新することにより行われます。 <xref:Microsoft.AnalysisServices.Partition> オブジェクトを削除するには、Drop メソッドを使用します。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Partition>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="AggregationDesign"></a> AggregationDesign オブジェクト  
 集計デザインは、<xref:Microsoft.AnalysisServices.AggregationDesign> オブジェクトの AggregationDesign メソッドを使用して構築します。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.AggregationDesign>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="Aggregation"></a> Aggregation オブジェクト  
 <xref:Microsoft.AnalysisServices.Aggregation> オブジェクトを作成するには、親メジャー グループの集計デザイン コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上の親メジャー グループ オブジェクトを更新します。 集計を <xref:Microsoft.AnalysisServices.AggregationCollection> から削除するには、Remove メソッドまたは RemoveAt メソッドを使用します。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Aggregation>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
## <a name="advanced-classes"></a>高度なクラス  
 高度なクラスは、キューブの構築や参照以外の OLAP 機能を提供します。 高度なクラスの一部とそれらの利点を以下に示します。  
  
-   アクション クラスは、キューブの特定領域の参照時に、アクティブな応答を作成するために使用します。  
  
-   主要業績評価指標 (KPI) : データの値を比較分析できます。  
  
-   パースペクティブ : 各ユーザーの必要性に応じて、1 つのキューブの特定のビューを参照できます。  
  
-   翻訳 : ユーザー ロケールに合わせてキューブをカスタマイズできます。  
  
-   プロアクティブ キャッシュ クラスは、MOLAP ストレージの拡張されたパフォーマンスと、ROLAP ストレージの即時性とのバランスをとり、定期的なパーティション処理を可能にします。  
  
 この拡張された動作の定義設定には AMO を使用しますが、実際の操作性は、これらすべての機能強化を実装したブラウザー クライアントによって定義されます。  
  
###  <a name="Action"></a> Action オブジェクト  
 <xref:Microsoft.AnalysisServices.Action> オブジェクトを作成するには、キューブのアクション コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.Cube> オブジェクトを更新します。 キューブの更新メソッドには、パラメーター UpdateOptions.ExpandFull を含めることができます。このパラメーターでは、この更新アクションによって、キューブ内で変更されたすべてのオブジェクトがサーバーに対して更新されます。  
  
 削除する、<xref:Microsoft.AnalysisServices.Action>オブジェクトをコレクションからこれを削除し、親キューブを更新する必要があります。  
  
 キューブを更新して処理するまで、アクションはクライアントから使用できません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Action>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="KPI"></a> Kpi オブジェクト  
 <xref:Microsoft.AnalysisServices.Kpi> オブジェクトを作成するには、キューブの KPI コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.Cube> オブジェクトを更新します。 キューブの Update メソッドには、パラメーター UpdateOptions.ExpandFull を含めることができます。このパラメーターでは、この更新アクションによって、キューブ内で変更されたすべてのオブジェクトがサーバーに対して更新されます。  
  
 削除する、<xref:Microsoft.AnalysisServices.Kpi>オブジェクト、これをコレクションから削除し、親キューブを更新する必要があります。  
  
 キューブを更新して処理するまで、KPI は使用できません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Kpi>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="Perspective"></a> Perspective オブジェクト  
 <xref:Microsoft.AnalysisServices.Perspective> オブジェクトを作成するには、キューブのパースペクティブコレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.Cube> オブジェクトを更新します。 キューブの Update メソッドには、パラメーター UpdateOptions.ExpandFull を含めることができます。このパラメーターでは、この更新アクションによって、キューブ内で変更されたすべてのオブジェクトがサーバーに対して更新されます。  
  
 <xref:Microsoft.AnalysisServices.Perspective> オブジェクトを削除するには、コレクションからこれを削除し、親キューブを更新する必要があります。  
  
 キューブを更新して処理するまで、パースペクティブは使用できません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Perspective>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="Translation"></a> Translation オブジェクト  
 <xref:Microsoft.AnalysisServices.Translation> オブジェクトを作成するには、対象オブジェクトの翻訳コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、最も近い主要な親オブジェクトをサーバー上で更新します。 最も近い親オブジェクトの Update メソッドには、パラメーター UpdateOptions.ExpandFull を含めることができます。このパラメーターでは、この更新アクションによって、変更されたすべての子オブジェクトがサーバーに対して更新されます。  
  
 <xref:Microsoft.AnalysisServices.Translation> オブジェクトを削除するには、コレクションからこれを削除し、最も近い親オブジェクトを更新する必要があります。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Translation>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
###  <a name="ProactiveCaching"></a> ProactiveCaching オブジェクト  
 <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトを作成するには、ディメンションまたはパーティションのプロアクティブ キャッシュ オブジェクト コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、ディメンション オブジェクトまたはパーティション オブジェクトをサーバー上で更新します。  
  
 <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトを削除するには、コレクションからこれを削除し、親オブジェクトを更新する必要があります。  
  
 ディメンションまたはパーティションを更新して処理するまで、プロアクティブ キャッシュは有効化も使用もできません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.ProactiveCaching>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](amo-classes-introduction.md)   
 [AMO OLAP 基本オブジェクトのプログラミング](programming-amo-olap-basic-objects.md)   
 [高度なオブジェクトをプログラミング AMO OLAP](programming-amo-olap-advanced-objects.md)   
 [論理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト&#40;Analysis Services - 多次元データ&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
