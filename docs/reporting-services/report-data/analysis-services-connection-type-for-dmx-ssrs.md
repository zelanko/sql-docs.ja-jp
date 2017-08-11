---
title: "Analysis Services DMX (SSRS) のための接続の種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters [Reporting Services], DMX
- Data Mining Prediction [Reporting Services]
- query view [Reporting Services]
- DMX [Reporting Services]
- design view [Reporting Services]
- data mining [Reporting Services]
- passing parameters [Reporting Services]
ms.assetid: 2de825e9-6d8a-4128-add0-da15dc6cea3e
caps.latest.revision: 64
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e4cb050e8f838eaab2bc215005b167c0dea258fc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="analysis-services-connection-type-for-dmx-ssrs"></a>DMX のための Analysis Services の接続の種類 (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースを使用してデータセットを作成した場合、レポート デザイナーで有効なキューブが検出されると、多次元式 (MDX) クエリ デザイナーが表示されます。 キューブは検出されなくても、データ マイニング モデルが使用可能な場合、レポート デザイナーではデータ マイニング拡張機能 (DMX) クエリ デザイナーが表示されます。 MDX と DMX デザイナー間には、をクリックして、**コマンドの種類 DMX** (![DMX クエリ言語ビューへの変更](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.gif "DMX クエリ言語ビューへの変更")) ツールバーのボタンをクリックします。 DMX クエリ デザイナーを使用すると、グラフィカルな要素を使用して対話的に DMX クエリを作成できます。 DMX クエリ デザイナーを使用するには、指定するデータ ソースが、データを提供するデータ マイニング モデルを既に備えている必要があります。 クエリ結果は、レポートで使用できるようにフラットな行セットに変換されます。  
  
> [!NOTE]  
>  レポートをデザインする前に、モデルのトレーニングを行う必要があります。 詳細については、「 [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)」を参照してください。  
  
## <a name="design-mode"></a>デザイン モード  
 DMX クエリ デザイナーは、デザイン モードで開きます。 デザイン モードには、単一のデータ マイニング モデルと入力テーブルを選択するためのグラフィカルなデザイン画面、および予測クエリを指定するためのグリッドが含まれています。 DMX クエリ デザイナーには、この他に、クエリ モードと結果モードの 2 つのモードがあります。 クエリ モードでは、デザインモードのグリッドがクエリ ペインに置き換えられ、これを使用して DMX クエリを入力することができます。 結果モードでは、クエリによって返された結果セットがデータ グリッドに表示されます。  
  
 DMX クエリ デザイナーのモードを変更するには、クエリのデザイン画面を右クリックし、 **[デザイン]**、 **[クエリ]**、または **[結果]**をクリックします。 詳細については、次を参照してください[Analysis Services DMX クエリ デザイナーのユーザー インターフェイス](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md)と[データ マイニング モデル (&) #40; DMX &#41; &#40; からのデータの取得。SSRS &#41;](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md).  
  
## <a name="designing-a-prediction-query"></a>予測クエリのデザイン  
 デザイン モードのクエリ デザイン ペインには、 **[マイニング モデル]** と **[入力テーブルの選択]**の 2 つのウィンドウがあります。 **[マイニング モデル]** ウィンドウでは、クエリで使用するマイニング モデルを選択します。 **[入力テーブルの選択]** ウィンドウでは、予測の基盤とするテーブルを選択します。 入力テーブルではなく、単一クエリを使用する場合は、クエリ デザイン ペインで右クリックし、 **[単一クエリ]**をクリックします。 **[入力テーブルの選択]** ウィンドウは、 **[単一クエリ入力]** ウィンドウに置き換えられます。  
  
 デザイン モードで、 **[マイニング モデル]** ウィンドウおよび **[入力テーブルの選択]** ウィンドウから、グリッド ペインの **[フィールド]** 列にフィールドをドラッグします。 また、残りの列に値を設定することによって、別名を指定したり、結果にフィールドを表示したり、複数のフィールドをグループにまとめたり、演算子を指定して特定の条件または引数でフィールド値を制限したりすることができます。 クエリ モードでは、フィールドをクエリ ペインにドラッグして DMX クエリを作成できます。  
  
## <a name="using-parameters"></a>パラメーターの使用  
 レポート パラメーターを DMX クエリ パラメーターに渡すことができます。 このためには、DMX クエリにパラメーターを追加し、 **[クエリ パラメーター]** ダイアログ ボックスでクエリ パラメーターを定義して、関連付けられたレポート パラメーターを変更します。 クエリ パラメーターを定義するのには、クリックして、**クエリ パラメーター** (![クエリ パラメーター ダイアログ ボックスのアイコン](../../reporting-services/report-data/media/iconqueryparameter.gif "クエリ パラメーター ダイアログ ボックスのアイコン")) ツールバーのボタンをクリックします。 DMX クエリでのパラメーターの定義については、「[Analysis Services の MDX クエリ デザイナーでのパラメーターの定義 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/define-parameters-in-the-mdx-query-designer-for-analysis-services.md)」を参照してください。  
  
 レポート パラメーターとクエリのパラメーター間のリレーションシップを管理する方法の詳細については、次を参照してください[クエリ パラメーター、レポート パラメーター &#40; への関連付け。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-data/associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md). パラメーターの詳細については、次を参照してください。[レポート パラメーターと #40 です。レポート ビルダーおよびレポート デザイナー &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>参照  
 [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)   
 [クエリ デザイン ツール (SSRS)](../../reporting-services/report-data/query-design-tools-ssrs.md)   
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
