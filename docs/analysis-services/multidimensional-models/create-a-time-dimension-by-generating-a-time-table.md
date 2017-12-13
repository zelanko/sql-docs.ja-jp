---
title: "時間テーブルを生成することによって時間ディメンションを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time dimensions [Analysis Services]
- dimensions [Analysis Services], time
- time periods [Analysis Services]
- range-based time dimensions [Analysis Services]
- server time dimensions [Analysis Services]
- calendars [Analysis Services]
- table-based time dimensions [Analysis Services]
ms.assetid: 58303326-1361-4c0e-9f3d-642ce69c4f6a
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: efd1341424c3be0bfd3aad5cf7c216c5303e250b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-a-time-dimension-by-generating-a-time-table"></a>Create a Time Dimension by Generating a Time Table
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、ディメンション ウィザードを使用することができます[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に時間テーブルを使用できない場合、ソース データベースでは、時間ディメンションを作成します。 この操作を行うには、 **[作成方法の選択]** ページで次のいずれかのオプションを選択します。  
  
-   **[データ ソースに時間テーブルを生成]** 基になるデータ ソースにオブジェクトを作成する権限がある場合に、このオプションを選択します。 ウィザードによって時間テーブルが生成され、このテーブルがデータ ソースに格納されます。 次に、ウィザードによってこの時間テーブルから時間ディメンションが作成されます。  
  
-   **[サーバーに時間テーブルを生成]** 基になるデータ ソースにオブジェクトを作成する権限がない場合に、このオプションを選択します。 ウィザードによってテーブルが生成され、データ ソースではなくサーバーに格納されます (時間テーブルからサーバーに作成されたディメンションを*サーバー時間ディメンション*と呼びます)。次に、ウィザードによってこのテーブルからサーバー時間ディメンションが作成されます。  
  
 時間ディメンションを作成する場合は、時間間隔と、ディメンションの開始日および終了日を指定します。 ウィザードでは、指定された時間間隔を使用して、時間属性を作成します。 ディメンションを処理すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では指定された日付と時間間隔のサポートに必要なデータを生成して格納します。 ウィザードでは、時間ディメンション用に作成された属性を使用して、ディメンションの階層が推奨されます。 この階層は、異なる時間間隔の関係を反映しており、また各種のカレンダーを考慮しています。 たとえば、標準のカレンダー階層では、週レベルは年レベルの下に表示されますが、月レベルの下には表示されません。これは、週は年に均一に分割されますが、月には均一に分割されないためです。 一方、製造カレンダーまたはレポート カレンダー階層では、週は均一に月に分割されるので、週レベルは月レベルの下に表示されます。  
  
## <a name="define-time-periods"></a>時間間隔の定義  
 ウィザードの **[時間間隔の定義]** ページを使用すると、ディメンション内に含める日付の範囲を指定できます。 たとえば、データの中で一番古い年の 1 月 1 日に始まり、現在の年の 1 年後または 2 年後に終わる (将来のトランザクションを可能にするため) 範囲を選択できます。 この範囲外のトランザクションは、そのディメンションの **UnknownMemberVisible** プロパティ設定によって、表示されないか、またはディメンション内で不明メンバーとして表示されます。 また、データで使用する週の開始日を変更することもできます (既定では日曜に設定されます)。  
  
 年、半期、四半期、三半期、月、10 日間、週、日付など、ウィザードで階層を作成する際に使用し、データに適用する時間間隔を選択します。 最短でも、日付以上の時間間隔を選択する必要があります。 Date 属性はディメンションのキー属性であるので、この属性がないとディメンションは機能できません。  
  
 **[時間メンバー名の言語]**の横で、ディメンションのメンバーのラベル付けに使用する言語を選択します。  
  
 日付範囲に基づいた時間ディメンションを作成した後は、ディメンション デザイナーを使用して、時間属性を追加または削除できます。 Date 属性はこのディメンションのキー属性であるため、この属性を削除することはできません。 Date 属性をユーザーに対して非表示にするには、この属性の **AttributeHierarchyVisible** プロパティを **False**に設定します。  
  
## <a name="select-calendars"></a>カレンダーの選択  
 1 月 1 日に始まり 12 月 31 日に終わる標準 (グレゴリオ暦) の 12 か月のカレンダーは、時間ディメンションの作成時に常に含まれます。 ウィザードの **[カレンダーの選択]** ページでは、ディメンション内の階層の基になるカレンダーをさらに指定できます。 カレンダーの種類の説明については、「 [日付型ディメンションの作成](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md)」をご覧ください。  
  
 ウィザードの **[時間間隔の定義]** ページで選択した時間間隔に応じ、カレンダーの選択によって、ディメンションに作成される属性が決定されます。 たとえば、ウィザードの **[時間間隔の定義]** ページで **[年]** と **[四半期]** の時間間隔を選択し、 **[カレンダーの選択]** ページで **[会計カレンダー]** を選択した場合は、会計カレンダーに対して FiscalYear、FiscalQuarter、および FiscalQuarterOfYear 属性が作成されます。  
  
 また、カレンダーに対して作成される属性で構成されるカレンダー固有の階層も作成されます。 カレンダーごとに、各階層の各レベルがその上のレベルにロール アップされます。 たとえば、標準の 12 か月カレンダーでは、ウィザードによって、Years と Weeks または Years と Months という階層が作成されます。 ただし、標準のカレンダーでは月ごとの週の数は同じではありません。したがって、Years、Months、および Weeks の階層はありません。 これに対して、レポートまたは製造カレンダーでは、週は各月に均等に割り当てられています。したがって、これらのカレンダーの週は月にロール アップされます。  
  
## <a name="completing-the-dimension-wizard"></a>ディメンション ウィザードの完了  
 **[ウィザードの完了]** ページで、ウィザードによって作成された属性と階層を確認し、時間ディメンションに名前を付けます。 **[完了]** をクリックしてウィザードを終了し、ディメンションを作成します。 ディメンションが完成したら、ディメンション デザイナーを使用してそのディメンションを変更できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [日付型ディメンションを作成します。](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md)   
 [データベース ディメンションのプロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)   
 [ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [データ ソースに時間テーブル以外のテーブルを生成することによるディメンションの作成](../../analysis-services/multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  
