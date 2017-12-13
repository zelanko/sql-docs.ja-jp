---
title: "多次元データベース (Analysis Services) の名前変更 |Microsoft ドキュメント"
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
helpviewer_keywords: renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6c56fc4d10e29e377b1b55330ec3badce57723f6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="rename-a-multidimensional-database-analysis-services"></a>多次元データベース名の変更 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]名前を変更する方法、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースに接続する方法によって異なります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 既存のデータベースの名前を変更するには、オンライン モードでデータベースに接続する必要があります。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内のオブジェクトがインスタンス化されるデータベースの名前を変更するには、プロジェクト モードで接続する必要があります。  
  
### <a name="to-change-the-database-name-in-online-mode"></a>オンライン モードでデータベース名を変更するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに直接接続します。  
  
2.  ソリューション エクスプローラーでデータベースを右クリックし、 **[データベースの編集]**をクリックします。  
  
3.  **[データベース名]** ボックスでデータベース名を変更します。  
  
4.  ツール バーの **[保存]** または **[すべてを保存]** をクリックし、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** または **[すべてを保存]** をクリックします。あるいは、 **データベース デザイナー** を終了し、メッセージが表示されたら **[保存]** をクリックします。  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのデータベース名が更新され、ソリューション エクスプローラーのデータベース オブジェクトが更新されます。  
  
### <a name="to-change-the-database-name-in-project-mode"></a>プロジェクト モードでデータベース名を変更するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[プロパティ ページ]** ダイアログ ボックスで、 **[構成プロパティ]** セクションの **[配置]** をクリックします。  
  
4.  **[データベース]** プロパティを新しいデータベース名に変更します。  
  
     次回 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトが配置されるときには、この新しい名前のデータベースにプロジェクトが配置されます。 この名前のデータベースが既に存在する場合は上書きされます。  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>SQL Server Management Studio を使用してデータベース名を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを右クリックし、Name プロパティを編集します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [多次元データベースのプロパティ &#40; を設定します。Analysis Services &#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
