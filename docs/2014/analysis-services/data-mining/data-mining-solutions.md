---
title: データマイニングソリューション |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 226b8c52fde4c9c4190c9c6c0c1e91c578643f53
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522733"
---
# <a name="data-mining-solutions"></a>データ マイニング ソリューション
  データ マイニング ソリューションとは、データ マイニング プロジェクトを少なくとも 1 つ含んだ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ソリューションです。  
  
 このセクションのトピックでは、を使用して、統合データマイニングソリューションを設計および実装する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 データ マイニング デザイン プロセスおよび関連ツールの概要については、「 [データ マイニングの概念](data-mining-concepts.md)」を参照してください。  
  
 データ マイニングに利用できるその他のプロジェクト タイプの詳細については、「 [データ マイニング ソリューションの関連プロジェクト](data-mining-solutions.md)」を参照してください。  
  
 [リレーショナル データ ソースと多次元ソリューションの比較](#bkmk_RelMD)  
  
 [データ マイニング ソリューションの配置](#bkmk_Deploy)  
  
 [ソリューションのチュートリアル](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a>リレーショナルソリューションと多次元ソリューションの比較  
 データマイニングソリューションは、多次元データ (既存のキューブ)、純粋なリレーショナルデータ (データウェアハウスのテーブルとビューなど)、またはテキストファイル、Excel ブック、またはその他の外部データソースに基づいて作成できます。  
  
-   既存の多次元データベース ソリューション内でデータ マイニング オブジェクトを作成できます。  
  
     通常、このようなソリューションは、既に作成済みのキューブが存在し、そのキューブをデータ ソースとしてデータ マイニングを実行する場合に作成します。 キューブに基づくモデルを移動したりバックアップしたりする際は、キューブも移動またはコピーする必要があります。  
  
-   データ マイニング オブジェクト (補助的なデータ ソースやデータ ソース ビューを含む) だけを含み、リレーショナル データ ソースのみを使用するデータ マイニング ソリューションを作成できます。  
  
     これはデータ マイニング モデルの作成に適した方法です。一般に、処理やクエリは、リレーショナル データ ソースがその対象である場合に最も高速になります。 また、サーバー間でのモデルの移動とバックアップも、EXPORT コマンドや IMPORT コマンドを使用して簡単に実行できます。  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a>データマイニングソリューションの配置  
 ソリューションの配置先となる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、多次元オブジェクトとデータ マイニング オブジェクトをサポートするモードで実行されている必要があります。つまり、テーブル モデルや PowerPivot データをホストするインスタンスにデータ マイニング オブジェクトを配置することはできません。  
  
 したがって、Visual Studio でデータ マイニング ソリューションを作成するときは、 **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを必ず使用してください。  
  
 ソリューションを配置すると、データ マイニングに使用されるオブジェクトが、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに作成されます。作成先は、ソリューション ファイルと同じ名前のデータベースになります。  
  
 リレーショナル ソリューションと多次元ソリューションの両方を配置する方法の詳細については、「 [データ マイニング ソリューションの配置](deployment-of-data-mining-solutions.md)」を参照してください。  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a>ソリューションのチュートリアル  
 データ マイニング ウィザードを使用してデータ マイニング ソリューションを作成する方法の概要について説明します。  
  
 [Create a Relational Mining Structure](create-a-relational-mining-structure.md)  
 マイニング構造は、リレーショナル データやテキスト ファイルのほか、データ ソース ビューに組み込むことのできる各種のソースから作成できます。  
  
 [Create an OLAP Mining Structure](create-an-olap-mining-structure.md)  
 OLAP キューブのデータを基にマイニング構造を作成します。 OLAP データから作成したモデルは、データ マイニング ディメンションとして保存できるほか、データ セットやモデルを新しいキューブとして保存することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ マイニング プロジェクト](data-mining-projects.md)  
  
 [データ マイニング オブジェクトの処理](processing-data-mining-objects.md)  
  
 [データ マイニング ソリューションの関連プロジェクト](data-mining-solutions.md)  
  
 [データ マイニング ソリューションの配置](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a>関連タスクおよびトピック  
 データ ソースとマイニング構造を含む基本的なデータ マイニング ソリューションを作成したら、そのソリューションを基礎として、新しいモデルの追加、モデルのテストや比較、予測の作成、データのサブセットに対する実験などを行うことができます。  
  
 詳細については、次のリンクを参照してください。  
  
|タスク|トピック|  
|-----------|------------|  
|作成するモデルのテスト、トレーニング データの質の検証、データ マイニング モデルの精度を表すグラフの作成|[テストおよび検証 &#40;データ マイニング&#41;](testing-and-validation-data-mining.md)|  
|構造および関連モデルにデータを取り込むことによるモデルのトレーニング (新しいデータでのモデルの更新と拡張)|[データ マイニング オブジェクトの処理](processing-data-mining-objects.md)|  
|マイニング モデルのカスタマイズ (トレーニング データへのフィルターの適用、異なるアルゴリズムの選択、高度なアルゴリズム パラメーターの設定)|[マイニング モデルとマイニング構造のカスタマイズ](customize-mining-models-and-structure.md)|  
|モデルのトレーニング用データにフィルターを適用することによるマイニング モデルのカスタマイズ|[マイニング モデルを構造に追加する &#40;Analysis Services - データ マイニング&#41;](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|データ マイニング ソリューションの更新と管理|Link TBD|  
  
## <a name="see-also"></a>参照  
 [データ マイニングのチュートリアル &#40;Analysis Services&#41;](../data-mining-tutorials-analysis-services.md)  
  
  
