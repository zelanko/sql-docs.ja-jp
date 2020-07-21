---
title: Visio のデータマイニング図形 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d30456ac3685aa3dc40af6f1c79f92796fc1404
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525778"
---
# <a name="data-mining-shapes-for-visio"></a>Visio 用のデータ マイニング図形
  Visio 用データ マイニング図形は、データ マイニング モデルを表示するためにカスタマイズされたテンプレートです。 これらのテンプレートを使用すると、作成したモデルに接続し、インタラクティブなプレゼンテーションを作成してデータ マイニングの結果を示すことができます。  
  
 テンプレートには、静的グラフや画面キャプチャよりも多くの利点があります。これらは、Analysis Services のインスタンスに格納されている基になるデータマイニングモデルと対話し、マイニングモデルのパターンの表示方法をカスタマイズできます。 ツリー モデルはレベルの折りたたみと展開ができ、データ ノードに対して、または属性別にフィルター処理を実行できるほか、確率や係数などのモデル統計を表示することもできます。  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Visio テンプレートには、以下のウィザードが含まれています:  
  
-   **依存関係ネットワークダイアグラム:** このウィザードを使用して、デシジョンツリーとニューラルネットワークのグラフを作成します。  
  
-   **デシジョンツリーダイアグラム:** このウィザードを使用すると、デシジョンツリーモデルに関連付けられている決定ポイントと数式を示すダイアグラムを作成できます。 このダイアグラムは、回帰モデルでも使用できます。  
  
-   **クラスターダイアグラム:** このウィザードを使用して、セグメンテーションモデルのカラフルなグラフを作成します。 属性の識別、プロファイル、依存関係などのビューを切り替え、クラスターの外観をカスタマイズすることができます。  
  
## <a name="installation"></a>インストール  
 Visio 用のデータマイニングテンプレートをインストールすると、既定では、次のファイルが \<drive> SQL Server 2012 DM アドイン (または、または \<drive> Program files (x86) \Microsoft SQL SERVER 2012 dm アドイン) にインストールされます。  
  
-   **Microsoft データマイニング. vst**このテンプレートには、データマイニング図形の操作に役立つ、デザイン済みの書式設定、レイアウト、およびウィザードが含まれています。  
  
-   **Microsoft データマイニング図形 Studio .vss**このステンシルファイルには、テンプレートに関連付けられた図形が含まれています。  
  
## <a name="how-to-use-the-templates"></a>テンプレートの使用方法  
 テンプレートを開くには、図形ファイルをダブルクリックするか、Visio を開いてから図形テンプレートを開きます。  
  
1.  Visio データ マイニング図形をステンシルから新しいページにドロップします。  
  
2.  ウィザードが起動したら、表示するデータ マイニング モデルがあるサーバーに接続します。  
  
3.  データ マイニング モデルを選択して、モデルの種類を視覚化の種類と一致させます。  
  
4.  データの表示オプションと書式設定オプションを設定します。  
  
5.  **データマイニング図形ウィザード**を完了すると、Visio の機能を使用して変更および強化できるダイアグラムが表示されます。  
  
 Visio モデル図を使用および強化する方法の詳細については、「 [visio でのデータマイニングモデルの表示 &#40;データマイニングアドイン](viewing-data-mining-models-in-visio-data-mining-add-ins.md)」を参照してください&#41;  
  
## <a name="requirements"></a>要件  
  
-   テンプレートを使用するには、最初に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成する必要があります。  
  
     ウィザードに従って、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーを選択し、マイニング モデルが格納されているデータベースを指定します。  
  
     接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
-   テーブル分析ツールを使用している場合は、モデルをサーバーに保存し、一時的なモデルを使用しないようにしてください [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。  
  
-   モデルは、サポートされているアルゴリズム (クラスタリング、デシジョン ツリー、ニューラル ネットワーク、Naïve Bayes、またはロジスティック回帰) を使用して作成されている必要があります。  
  
  
