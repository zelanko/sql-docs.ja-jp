---
title: "Kpi |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a38d562df467f020db529fde8633acaa081d045c
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="kpis"></a>KPI
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
*KPI* (主要業績評価指標) は、表形式モデルで、 *対象* の値に対する *ベース* メジャーによって定義される、また、メジャーまたは絶対値によって定義される値のパフォーマンスの測定に使用されます。 この記事は、表形式モデルの作成者が表形式モデルの Kpi の基本を理解を提供します。  
  
##  <a name="bkmk_benefits"></a> 利点  
 ビジネス用語では、主要業績評価指標 (KPI) とは、ビジネス目標を判断するための測定値のことです。 KPI は一定期間中頻繁に評価されます。 たとえば、組織の営業部門では KPI を使用して予測総利益に対する月間売上総利益を測定できます。 経理部門では、月間の収入に対する支出を測定してコストを評価し、人事部門では、四半期単位の従業員離職率を測定することができます。 これらはそれぞれ KPI の一例です。 企業のプロフェッショナルは、グループにまとめて事業のスコアカードに記録した KPI を頻繁に使用し、事業の成功度の履歴要約をすばやく正確に取得したり、傾向を把握したりします。  
  
 表形式モデルの KPI には次のものが含まれます。  
  
 **ベース値**  
 ベース値は、値に解決されるメジャーによって定義されます。 ベース値には、実績販売の集計や、特定期間の利益などの計算メジャーなどを使用できます。  
  
 **対象の値**  
 対象の値は、値に解決されるメジャーまたは絶対値によって定義されます。 たとえば、組織の経営層が目標とする売上または利益の増加額を対象の値にすることができます。  
  
 **状態のしきい値**  
 状態のしきい値は、低いしきい値と高いしきい値との間の範囲によって、または固定値によって定義されます。 状態のしきい値は、対象の値と比べたベース値の状態を簡単に判別できるようにグラフィックで表示されます。  
  
##  <a name="bkmk_example"></a> 例  
 Adventure Works の販売責任者は、販売担当者の一定期間 (年) の販売ノルマの達成状況がひとめでわかるようなピボットテーブルを作成しようとしています。 ピボットテーブルには販売担当者ごとの実績販売額 (ドル) と販売ノルマ額 (ドル) を表示し、各担当者がノルマを下回っているか、上回っているかの状態を示す簡単なグラフィックを表示することにします。 データは年単位でスライスできるようにしたいと考えています。  
  
 これを実現するために、組織の BI ソリューション開発者にサポートを依頼し、AdventureWorks 表形式モデルに販売 KPI を追加することにします。 販売責任者、Adventure Works 表形式モデル データ ソースに接続し、フィールド (メジャーと KPI) と、営業担当者がノルマを達成するかどうかを分析するスライサーをピボット テーブルを作成する Excel が使用されます。  
  
 モデルの FactResellerSales テーブルの SalesAmount 列に、各販売担当者の実績販売額をドル単位で表すメジャーが作成されます。 このメジャーは KPI のベース値を定義します。  
  
 次の式で販売メジャーを作成します。  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 FactSalesQuota テーブルの SalesAmountQuota 列には、各担当者の販売ノルマが定義されています。 この列の値が KPI の対象のメジャー (値) になります。  
  
 次の式で SalesAmountQuota メジャーを作成します。  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  FactSalesQuota テーブルの EmployeeKey 列と DimEmployees テーブルの EmployeeKey 列との間にリレーションシップがあります。 このリレーションシップは、DimEmployee テーブルの各販売担当者を FactSalesQuota テーブルで表すために必要です。  
  
 KPI のベース値および対象の値となるメジャーを作成した後は、販売メジャーを新しい販売 KPI に拡張します。 販売 KPI では、ターゲットの SalesAmountQuota メジャーが対象の値として定義されます。 状態のしきい値はパーセンテージ範囲によって定義されます。ターゲットが 100% の場合、販売メジャーによって定義された実績販売額がターゲットの SalesAmoutnQuota メジャーで定義されたノルマに達したことを意味します。 [低] および [高] のパーセンテージはステータス バーで定義され、グラフィックの種類が選択されます。  
  
 これで、販売責任者は KPI のベース値、対象の値、状態を [値] フィールドに追加するピボットテーブルを作成できます。 Employees 列を RowLabel フィールドに追加し、CalendarYear 列をスライサーとして追加します。  
  
 販売責任者は、各販売担当者の実績販売額、販売ノルマ、状態を年単位でスライスできるようになりました。 これによって数年間の売上傾向を分析し、販売担当者の販売ノルマを調整する必要があるかどうかを判断できます。  
  
##  <a name="bkmk_create"></a> Create and edit KPIs  
 KPI を作成するには、モデル デザイナーの [主要業績評価指標] ダイアログ ボックスを使用します。 KPI はメジャーと関連付ける必要があるため、ベース値を評価するメジャーを拡張してから、対象の値を評価するメジャーを作成するか、絶対値を入力することにより、KPI を作成します。 ベース メジャー (値) および対象の値が定義された後、状態のしきい値のパラメーターをベース値と対象の値の間で定義できます。 状態は、選択可能なアイコン、バー、グラフ、または色を使用して、グラフィカルな形式で表示されます。 ベース値および対象の値は、状態と同様に、他のデータ フィールドに対してスライスできる値として、レポートまたはピボットテーブルに追加できます。  
  
 [主要業績評価指標] ダイアログ ボックスを表示するには、テーブルのメジャー グリッドで、ベース値として機能するメジャーを右クリックし、 **[KPI の作成]**をクリックします。 ベース値としての KPI にメジャーが拡張された後、メジャー グリッドのメジャー名の横にアイコンが表示され、メジャーが KPI に関連付けられていることを示します。  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|トピック|Description|  
|-----------|-----------------|  
|[KPI の作成および管理](../../analysis-services/tabular-models/create-and-manage-kpis-ssas-tabular.md)|ベース メジャー、対象のメジャー、および状態のしきい値と共に KPI を作成する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [メジャー](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
