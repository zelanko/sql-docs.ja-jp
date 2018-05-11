---
title: データ マイニング ソリューション |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f1027c4c7aa71b22ddc68495302a270e4e0f105a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="data-mining-solutions"></a>データ マイニング ソリューション
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング ソリューションとは、データ マイニング プロジェクトを少なくとも 1 つ含んだ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ソリューションです。  
  
 このセクションの各トピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を使用した統合データ マイニング ソリューションの設計と実装の方法について説明します。 データ マイニング デザイン プロセスおよび関連ツールの概要については、「 [データ マイニングの概念](../../analysis-services/data-mining/data-mining-concepts.md)」を参照してください。  
  
 データ マイニングに利用できるその他のプロジェクト タイプの詳細については、「[データ マイニング ソリューションの関連プロジェクト](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)」を参照してください。  
  
 [リレーショナル データ ソースとします。多次元ソリューション](#bkmk_RelMD)  
  
 [データ マイニング ソリューションの配置](#bkmk_Deploy)  
  
 [ソリューションのチュートリアル](#bkmk_Walkthru)  
  
##  <a name="bkmk_RelMD"></a>リレーショナル データ ソースとします。多次元ソリューションの比較  
 データ マイニング ソリューションには、多次元データ (既存のキューブ) のほか、純粋なリレーショナル データ (データ ウェアハウス内のテーブルやビュー)、テキスト ファイル、Excel ブック、さらには、外部データ ソースを使用することもできます。  
  
-   既存の多次元データベース ソリューション内でデータ マイニング オブジェクトを作成できます。  
  
     通常、このようなソリューションは、既に作成済みのキューブが存在し、そのキューブをデータ ソースとしてデータ マイニングを実行する場合に作成します。 キューブに基づくモデルを移動したりバックアップしたりする際は、キューブも移動またはコピーする必要があります。  
  
-   データ マイニング オブジェクト (補助的なデータ ソースやデータ ソース ビューを含む) だけを含み、リレーショナル データ ソースのみを使用するデータ マイニング ソリューションを作成できます。  
  
     これはデータ マイニング モデルの作成に適した方法です。一般に、処理やクエリは、リレーショナル データ ソースがその対象である場合に最も高速になります。 また、サーバー間でのモデルの移動とバックアップも、EXPORT コマンドや IMPORT コマンドを使用して簡単に実行できます。  
  
##  <a name="bkmk_Deploy"></a> データ マイニング ソリューションの配置  
 ソリューションの配置先となる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、多次元オブジェクトとデータ マイニング オブジェクトをサポートするモードで実行されている必要があります。つまり、テーブル モデルや [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データをホストするインスタンスにデータ マイニング オブジェクトを配置することはできません。  
  
 したがって、Visual Studio でデータ マイニング ソリューションを作成するときは、 **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを必ず使用してください。  
  
 ソリューションを配置すると、データ マイニングに使用されるオブジェクトが、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに作成されます。作成先は、ソリューション ファイルと同じ名前のデータベースになります。  
  
 リレーショナル ソリューションと多次元ソリューションの両方を配置する方法の詳細については、「 [データ マイニング ソリューションの配置](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)」を参照してください。  
  
##  <a name="bkmk_Walkthru"></a> ソリューションのチュートリアル  
 データ マイニング ウィザードを使用してデータ マイニング ソリューションを作成する方法の概要について説明します。  
  
 [リレーショナル マイニング構造を作成します。](../../analysis-services/data-mining/create-a-relational-mining-structure.md)  
 マイニング構造は、リレーショナル データやテキスト ファイルのほか、データ ソース ビューに組み込むことのできる各種のソースから作成できます。  
  
 [OLAP マイニング構造を作成します。](../../analysis-services/data-mining/create-an-olap-mining-structure.md)  
 OLAP キューブのデータを基にマイニング構造を作成します。 OLAP データから作成したモデルは、データ マイニング ディメンションとして保存できるほか、データ セットやモデルを新しいキューブとして保存することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ マイニング プロジェクト](../../analysis-services/data-mining/data-mining-projects.md)  
  
 [データ マイニング オブジェクトの処理](../../analysis-services/data-mining/processing-data-mining-objects.md)  
  
 [データ マイニング ソリューションの関連プロジェクト](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)  
  
 [データ マイニング ソリューションの配置](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a>関連タスクおよびトピック  
 データ ソースとマイニング構造を含む基本的なデータ マイニング ソリューションを作成したら、そのソリューションを基礎として、新しいモデルの追加、モデルのテストや比較、予測の作成、データのサブセットに対する実験などを行うことができます。  
  
 詳細については、次のリンクを参照してください。  
  
|処理手順|トピック|  
|-----------|------------|  
|作成するモデルのテスト、トレーニング データの質の検証、データ マイニング モデルの精度を表すグラフの作成|[テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)|  
|構造および関連モデルにデータを取り込むことによるモデルのトレーニング (新しいデータでのモデルの更新と拡張)|[データ マイニング オブジェクトの処理](../../analysis-services/data-mining/processing-data-mining-objects.md)|  
|マイニング モデルのカスタマイズ (トレーニング データへのフィルターの適用、異なるアルゴリズムの選択、高度なアルゴリズム パラメーターの設定)|[マイニング モデルおよび構造体をカスタマイズします。](../../analysis-services/data-mining/customize-mining-models-and-structure.md)|  
|モデルのトレーニング用データにフィルターを適用することによるマイニング モデルのカスタマイズ|[マイニング モデル構造体 & #40; を追加します。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|データ マイニング ソリューションの更新と管理|Link TBD|  
  
## <a name="see-also"></a>参照  
 [データ マイニングのチュートリアル & #40 です。Analysis Services & #41;](../../analysis-services/data-mining-tutorials-analysis-services.md)  
  
  
