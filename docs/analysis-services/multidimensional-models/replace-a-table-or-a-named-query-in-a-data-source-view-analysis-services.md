---
title: "テーブルまたはデータ ソース ビュー (Analysis Services) の名前付きクエリを置換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c8d82321d439301915c4c0b50234293f628dc94d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a>データ ソース ビュー内のテーブルまたは名前付きクエリの置換 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ ソース ビュー デザイナーで別のテーブルまたはビューから、同じまたは別のデータ ソース、または、DSV で定義されている名前付きクエリを使用して、テーブル、ビュー、またはデータ ソース ビュー (DSV) の名前付きクエリを置き換えることができます。 テーブルを置換した場合、DSV 内のテーブルのオブジェクト ID は変更されないので、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースまたはプロジェクト内でそのテーブルを参照している他のすべてのオブジェクトは、引き続きそのテーブルを参照します。 名前や列の型の一致に基づいて、引き続き関連のあるリレーションシップは維持されます。 これに対して、テーブルを削除して追加した場合、参照とリレーションシップは失われるので、再作成する必要があります。  
  
 テーブルを別のテーブルに置換するには、プロジェクト モードのデータ ソース ビュー デザイナー内のソース データに対するアクティブな接続が必要です。  
  
 データ ソース ビュー内のテーブルをデータ ソース内の別のテーブルに置換することが最も頻繁に行われます。 ただし、名前付きクエリをテーブルに置換することもできます。 たとえば、以前にテーブルを名前付きクエリに置換し、今回はテーブルに戻す場合があります。  
  
> [!IMPORTANT]  
>  データ ソース内のテーブルの名前を変更した場合は、DSV を更新する前に、テーブルの置換手順を実行し、名前を変更したテーブルを DSV 内の対応するテーブルのソースとして指定します。 置換および名前変更の手順を行うと、DSV 内のテーブル、テーブルの参照、およびテーブルのリレーションシップは維持されます。 この手順を実行しないと、DSV を更新したときに、データ ソース内の名前を変更したテーブルは削除されたと見なされます。 詳細については、「[データ ソース ビューでのスキーマの更新 (Analysis Services)](../../analysis-services/multidimensional-models/refresh-the-schema-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
##  <a name="bkmk_nq"></a> テーブルを名前付きクエリで置換する  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、テーブルまたは名前付きクエリを置換するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。  
  
3.  **[名前付きクエリの作成]** ダイアログ ボックスを開きます。 **[テーブル]** または **ダイアグラム** ペインで、置換するテーブルを右クリックし、 **[テーブルの置換]** をポイントして **[新しい名前付きクエリの使用]**をクリックします。  
  
4.  **[名前付きクエリの作成]** ダイアログ ボックスで名前付きクエリを定義し、 **[OK]**をクリックします。  
  
5.  変更したデータ ソース ビューを保存します。  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a>テーブルまたは名前付きクエリを別のテーブルで置換する  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、テーブルまたは名前付きクエリを置換するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。  
  
3.  **[テーブルと他のテーブルとの置換]** ダイアログ ボックスを開きます。 **[テーブル]** または **ダイアグラム** ペインで、置換するテーブルまたは名前付きクエリを右クリックし、 **[テーブルの置換]** をポイントして **[他のテーブルを使用]**をクリックします。  
  
4.  **[テーブルと他のテーブルとの置換]** ダイアログ ボックスで、次の操作を実行します。  
  
    1.  **[データソース]** ボックスの一覧で、使用するデータ ソースを選択します。  
  
    2.  テーブルまたは名前付きクエリを置換するテーブルを選択します。  
  
5.  **[OK]** をクリックします。  
  
6.  変更したデータ ソース ビューを保存します。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
