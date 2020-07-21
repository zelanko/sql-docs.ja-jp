---
title: データマイニング (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 447b350aae97ded341788dd4b398441d6b1efdb2
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522703"
---
# <a name="data-mining-ssas"></a>データ マイニング (SSAS)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、データ マイニングを取り入れたソリューションのための統合プラットフォームを提供します。 リレーショナル データまたはキューブ データを使用して、予測分析を含むビジネス インテリジェンス ソリューションを作成できます。  
  
## <a name="benefits-of-data-mining"></a>データ マイニングの利点  
 データ マイニングでは、詳細な研究に基づいた統計原則を使用してデータ内のパターンを検出します。複雑な問題に関して合理的な意思決定を行う場合に、この情報を役立てることができます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータ マイニング アルゴリズムをデータに適用することにより、傾向の予測、パターンの識別、およびルールや提案の作成を行い、複雑なデータ セット内でイベントの順序を分析し、新しい見識を得ることができます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のデータ マイニングは、強力でありながら使いやすく、分析用やレポート作成用として多くの人に使用されているツールに統合されています。 データ マイニングの使用を開始するために必要な全体像を把握するには、このセクションのリンクを参照してください。  
  
## <a name="key-data-mining-features"></a>データ マイニングの主要機能  
 SQL Server では、統合データ マイニング ソリューションをサポートするために次の機能が提供されています。  
  
-   複数のデータ ソース: データ マイニングを行うためにデータ ウェアハウスや OLAP キューブを作成する必要はありません。 外部プロバイダー、スプレッドシート、テキスト ファイルから、表形式のデータを使用できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で作成した OLAP キューブを簡単にマイニングすることもできます。 ただし、インメモリ データベースからのデータは使用できません。  
  
-   統合されたデータ クレンジング、データ管理、および ETL: データのプロファイリングおよびクレンジングのための高度なツールが Data Quality Services によって提供されます。 Integration Services を使用して、データのクレンジングおよびモデルの構築、処理、トレーニング、および更新のために、ETL プロセスを構築できます。  
  
-   複数のカスタマイズ可能なアルゴリズム: クラスタリング、ニューラル ネットワーク、デシジョン ツリーなどのアルゴリズムの提供に加え、このプラットフォームは、独自のカスタム プラグイン アルゴリズムの開発をサポートします。  
  
-   モデル テスト用インフラストラクチャ: 相互検証、分類マトリックス、リフト チャート、散布図などの重要な統計ツールを使用して、モデルおよびデータ セットをテストできます。 テストおよびトレーニングのセットを容易に作成および管理できます。  
  
-   クエリおよびドリルスルー: 予測クエリを作成し、モデルのパターンおよび統計情報を取得し、ケース データにドリルスルーします。  
  
-   クライアント ツール: SQL Server で提供される開発および設計スタジオに加え、Excel 用データ マイニング アドインを使用して、モデルの作成、照会、および参照を行うことができます。 Web サービスなど、カスタムのクライアントを作成することもできます。  
  
-   スクリプト言語サポートとマネージド API: データ マイニング オブジェクトはすべて、プログラム可能です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用の MDX 拡張機能、XMLA 拡張機能、または、PowerShell 拡張機能により、スクリプトの作成が可能です。 データ マイニング拡張機能 (DMX) 言語を使用すると、クエリとスクリプト作成を迅速に行うことができます。  
  
-   セキュリティおよび配置: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]により、ロール ベースのセキュリティが提供されます (モデルと構造データへのドリルスルーに、別々の権限を使用できるなど)。 他のサーバーへのモデルの配置が容易であるため、ユーザーがパターンにアクセスし、予測を実行することが可能になります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションのトピックでは、SQL Server データ マイニングの主要機能および関連タスクについて説明します。  
  
-   [データマイニングの概念](data-mining-concepts.md)  
  
-   [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [マイニング構造 (Analysis Services - データ マイニング)](mining-structures-analysis-services-data-mining.md)  
  
-   [マイニング モデル (Analysis Services - データ マイニング)](mining-models-analysis-services-data-mining.md)  
  
-   [テストおよび検証 &#40;データ マイニング&#41;](testing-and-validation-data-mining.md)  
  
-   [データマイニングクエリ](data-mining-queries.md)  
  
-   [データ マイニング ソリューション](data-mining-solutions.md)  
  
-   [データ マイニング ツール](data-mining-tools.md)  
  
-   [データ マイニングのアーキテクチャ](data-mining-architecture.md)  
  
-   [セキュリティの概要 &#40;データ マイニング&#41;](security-overview-data-mining.md)  
  
  
