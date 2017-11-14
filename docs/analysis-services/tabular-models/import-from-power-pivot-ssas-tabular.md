---
title: "Power Pivot (SSAS テーブル) からのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b85ae04b00034decd7390f86db1ee7e00c496434
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="import-from-power-pivot-ssas-tabular"></a>Power Pivot からのインポート (SSAS テーブル)
  このトピックでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からのインポート プロジェクト テンプレートを使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ブックからメタデータとデータをインポートし、新しいテーブル モデル プロジェクトを作成する方法を説明します。  
  
## <a name="create-a-new-tabular-model-from-a-power-pivot-for-excel-file"></a>Excel ファイルの Power Pivot から新しいテーブル モデルを作成する  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックからのインポートにより新しいテーブル モデル プロジェクトを作成すると、ブックの構造を定義するメタデータを使用して、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]にテーブル モデル プロジェクトの構造が作成および定義されます。 テーブル、列、メジャー、リレーションシップなどのオブジェクトは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにあるとおりにテーブル モデル プロジェクトで保持および表示されます。 .xlsx ブック ファイルに対する変更は行われません。  
  
> [!NOTE]  
>  リンク テーブルは、テーブル モデルではサポートされません。 リンク テーブルを含む [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックからインポートする場合、リンク テーブル データはコピー/貼り付けデータとして取り扱われ、Model.bim ファイルに保存されます。 コピー/貼り付けテーブルのプロパティを表示するとき、 **ソース データ** プロパティは無効であり、 **[テーブル]** メニューの **[テーブルのプロパティ]** ダイアログは無効です。  
>   
>  モデルに埋め込まれているデータに追加できる行数は 10,000 行に制限されています。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からモデルをインポートしたときに、"データが切り捨てられました。 貼り付けられたテーブルに含めることができるのは 10000 行までです。" というエラーが表示された場合は、SQL Server のテーブルなど、別のデータ ソースに埋め込みデータを移動することによって [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] モデルを変更してから、再インポートする必要があります。  
  
 ワークスペース データベースが、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と同じコンピューター (ローカル) の Analysis Services インスタンスにあるか、リモートの Analysis Services インスタンスにあるかにより、特に注意する点が変わります。  
  
 ワークスペース データベースが Analysis Services のローカル インスタンスにある場合は、メタデータとデータの両方を [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックからインポートできます。 メタデータはブックからコピーされて、テーブル モデル プロジェクトを作成するために使用されます。 データはブックからコピーされて、プロジェクトのワークスペース データベースに保存されます (Model.bim ファイルに保存されるコピー/貼り付けデータ以外)。  
  
 ワークスペース データベースが Analysis Services のリモート インスタンスにある場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel ブックからデータをインポートできません。 ブックのメタデータはインポートできますが、インポートすると、スクリプトがリモートの Analysis Services インスタンスで実行されます。 信頼できる [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックからのみ、メタデータをインポートする必要があります。 データは、データ ソース接続に定義されたソースからインポートする必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのコピー/貼り付けデータとリンク テーブル データは、テーブル モデル プロジェクトにコピーして貼り付ける必要があります。  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-power-pivot-for-excel-file"></a>Power Pivot for Excel ファイルからテーブル モデル プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]**をクリックし、 **[プロジェクト]**をクリックします。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** をクリックし、**[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からインポート]** をクリックします。  
  
3.  **[名前]**にプロジェクトの名前を入力し、場所とソリューション名を指定してから、 **[OK]**をクリックします。  
  
4.  **[ファイルを開く]** ダイアログ ボックスで、インポートするモデル メタデータおよびデータを含む [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ファイルを選択し、 **[開く]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ワークスペース データベース &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)   
 [コピーと貼り付けデータ & #40 です。SSAS テーブル &#41;](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)  
  
  

