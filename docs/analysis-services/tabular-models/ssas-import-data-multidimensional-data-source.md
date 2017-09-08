---
title: "多次元データ ソース (SSAS テーブル) からのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4aaa43e745c86cd493279fe8bd875d376f8185c0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---multidimensional-data-source"></a>データのインポート - 多次元データ ソース
  Analysis Services キューブ データベースは、テーブル モデルのデータ ソースとして使用できます。 Analysis Services キューブからデータをインポートするには、インポートするデータを選択するための MDX クエリを定義する必要があります。  
  
 SQL Server Analysis Services データベースに含まれている任意のデータをモデルにインポートできます。 ディメンションの一部またはすべてを抽出することも、キューブからスライスおよび集計 (現在の年の月ごとの売上合計など) を取得することもできます。ただし、キューブからインポートしたデータはすべてフラット化されていることに注意する必要があります。 したがって、複数のディメンションからメジャーを取得するクエリを定義した場合、インポートされるデータでは各ディメンションがそれぞれ別の列になります。  
  
 Analysis Services キューブのバージョンは、SQL Server 2005、SQL Server 2008、SQL Server 2008 R2、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]である必要があります。  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>Analysis Services キューブからデータをインポートするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]**をクリックします。  
  
2.  **[データ ソースへの接続]** ページで、 **[Microsoft Analysis Services]**を選択し、 **[次へ]**をクリックします。  
  
3.  テーブルのインポート ウィザードの手順に従って操作します。 **[MDX クエリの指定]** ページで MDX クエリを指定できます。 MDX クエリ デザイナーを使用するには、[MDX クエリの指定] ページで **[デザイン]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [データのインポート (SSAS テーブル)](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [サポートされているデータ ソース (SSAS テーブル)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
