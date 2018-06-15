---
title: 'レッスン 8: アクションの定義 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 50cc788fa39531c086049886a77f17920ae81e8f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017499"
---
# <a name="lesson-8-defining-actions"></a>レッスン 8 : アクションの定義
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

このレッスンでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトでアクションを定義する方法を学習します。 アクションは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に格納される多次元式 (MDX) ステートメントです。アクションはクライアント アプリケーションに統合することができ、ユーザーによって開始可能です。  
  
> [!NOTE]  
> このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。 途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。 このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](http://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。  
  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、次の表に示されている種類のアクションをサポートします。  
  
|||  
|-|-|  
|CommandLine|コマンド プロンプトでコマンドを実行します。|  
|データセット|データセットをクライアント アプリケーションに返します。|  
|ドリルスルー|ドリルスルー ステートメントを式として返します。この式は、行セットを返すときにクライアントによって実行されます。|  
|Html|インターネット ブラウザーで HTML スクリプトを実行します。|  
|[専用]|この一覧に表示されていないインターフェイスを使用して操作を実行します。|  
|レポート|パラメーター化された URL ベースの要求をレポート サーバーに送信して、レポートをクライアント アプリケーションに返します。|  
|[行セット]|行セットをクライアント アプリケーションに返します。|  
|ステートメントから削除してください。|OLE DB コマンドを実行します。|  
|[URL]|インターネット ブラウザーで動的 Web ページを表示します。|  
  
アクションを使用すると、アプリケーションを起動したり、選択したアイテムのコンテキスト内で他のステップを実行することができます。 詳細については、[「アクション (Analysis Services - 多次元データ)」](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md) および [「多次元モデルのアクション」](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md) を参照してください。  
  
> [!NOTE]  
> アクション例については、[計算ツール] ペインの [テンプレート] タブか、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW サンプル データ ウェアハウスのアクション例を参照してください。 このデータベースのインストールの詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](../analysis-services/install-sample-data-and-projects.md)」 を参照してください。  
  
このレッスンの内容は次のとおりです。  
  
[定義とドリルスルー アクションの使用](../analysis-services/lesson-8-1-defining-and-using-a-drillthrough-action.md)  
この作業では、このチュートリアルで以前に定義したファクト ディメンションのリレーションシップによって、ドリルスルー アクションの定義、使用、変更を行います。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 9: Defining Perspectives and Translations](../analysis-services/lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services のチュートリアル シナリオ](../analysis-services/analysis-services-tutorial-scenario.md)  
[多次元モデリング (Adventure Works チュートリアル)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[アクションと #40 です。Analysis Services - 多次元データ & #41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[「多次元モデルのアクション」](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
