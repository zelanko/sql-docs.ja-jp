---
title: SQL Server 2014 の分析サービス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 986356e6ebf7697bf0b425553f6803659a0fc5cb
ms.sourcegitcommit: 8f99d15c5b23d9f3c08a77e2b8bea5772f570493
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "80760304"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services は、意思決定支援およびビジネス インテリジェンス (BI) ソリューションで使用される分析データ エンジンであり、Excel、Reporting Services レポート、その他のサード パーティの BI ツールなどのビジネス レポートやクライアント アプリケーションの分析データを提供します。 

## <a name="about-sql-server-analysis-services-documentation"></a>SQL Server 分析サービスのドキュメントについて

ドキュメントはバージョン別に分離されています。 現在、SQL Server 2014 分析サービスのドキュメントを参照してください。

- SQL Server 2012 およびそれ以前のバージョンの詳細については[、SQL Server の以前のバージョンのドキュメント](https://docs.microsoft.com/previous-versions/sql/)を参照してください。
- SQL Server 2014 の詳細については[、「SQL Server](../2014-toc/index.yml) 2014 オンライン ブック」を参照してください。
- SQL Server 2016 およびそれ以降の詳細については[、Analysis サービスのドキュメントを参照してください](https://docs.microsoft.com/analysis-services/)。
- Azure 分析サービスの詳細については[、「Azure 分析サービスのドキュメント」を参照してください](https://docs.microsoft.com/azure/analysis-services/)。

## <a name="analysis-services-workflow"></a>分析サービス ワークフロー

一般的なワークフローには、OLAP または表形式のデータ モデルの構築、モデルをデータベースとしてサーバー インスタンスに配置、データを読み込むデータベースの処理、データ アクセスを許可する権限の割り当てなどが含まれます。 準備が完了すると、複数の用途を持つこのデータ モデルに、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をデータ ソースとしてサポートしている任意のクライアント アプリケーションがアクセスできるようになります。  
  
 モデルを作成するには、SQL Server データ ツール[(Analysis Services で使用されるツールとアプリケーション](tools-and-applications-used-in-analysis-services.md)を参照) を使用して、表形式または多次元およびデータ マイニング プロジェクト テンプレートを選択します。 プロジェクト テンプレートには、モデルで必要とされるすべてのオブジェクトのフォルダーが含まれています。 ウィザードを使用して、データ ソース、データ ソース ビュー、ディメンション、キューブ、ロールなど、すべての基本的な要素を作成することができます。  
  
 モデルは、外部データ システムから取得したデータによって作成されます。通常は外部データ システムとして、SQL Server または Oracle リレーショナル データベース エンジンでホストされているデータ ウェアハウスを使用します (テーブル モデルでは、追加のデータ ソースの種類もサポートされています)。 モデルは、キューブなどのクエリ オブジェクトを指定しますが、複数のキューブ、計算、KPI (ビジネス ロジック、ナビゲーションやドリルスルー動作などの相互作用をカプセル化する) で使用できるディメンションも指定します。  
  
 モデルを使用するには、特定のサーバー モードでデータベースを実行するサーバー インスタンスに展開され、Excel またはその他のアプリケーションを介して接続する承認されたユーザーがデータを使用できるようにします。  
  
 インスタンスは、次の 3 つのサーバー モードのいずれかでインストールできます。  
  
-   テーブル インスタンスとしてインストールし、テーブル モデルを実行します。  
  
-   多次元およびデータ マイニングのインスタンスとしてインストールし、OLAP キューブとデータ マイニング モデルを実行します (既定)。  
  
-   PowerPivot for SharePoint としてインストールし、SharePoint 上で PowerPivot と Excel データ モデルを実行します (PowerPivot for SharePoint は中間層のデータ エンジンであり、SharePoint でホストされているデータ モデルの読み込み、クエリ、更新を実行します)。  
  
 同じデータ エンジンを、3 つの方法で使用できます。 サーバー モードはインストール中に設定され、後で変更できないことに注意してください。 別のモードが必要な場合は、新しいインスタンスをインストールする必要があります。  
  
 Analysis Services に関する基本ドキュメントは、作成するプロジェクトの種類に対応するセクション別に分類されます。 それぞれのモードまたは機能領域の詳細については、次のリンクから選択してください。  
  
 **エリア別のコンテンツの参照**  
 [SSAS&#41;&#40;表形式および多次元ソリューションを比較する](comparing-tabular-and-multidimensional-solutions-ssas.md)![小さなファイル フォルダ アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")  
  
 ![小さなファイル フォルダ アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[分析サービス インスタンス管理](instances/analysis-services-instance-management.md)  
  
 [SSAS 表形式&#41;&#40;](tabular-models/tabular-models-ssas.md)![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")の表形式モデル  
  
 SSAS&#41;&#40;![小さいファイル フォルダ アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[多次元モデリング](multidimensional-models/multidimensional-models-ssas.md)  
  
 [SSAS&#41;&#40;](data-mining/data-mining-ssas.md)![小さなファイル フォルダ アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")データ マイニング  
  
 ![小さなファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [PowerPivot を &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能は、エディションによって異なります。 多次元およびデータ マイニング モデルは Standard Edition で使用できますが、上位エディションに比べると機能が少なくなっています。 テーブル モデルと PowerPivot for SharePoint はプレミアム機能であり、Standard Edition のライセンスでは使用できません。 詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SSAS&#41;&#40;分析サービスのチュートリアル](analysis-services-tutorials-ssas.md)   
 [SQL Server 2014 のインストール](../database-engine/install-windows/installation-for-sql-server.md)   
 [開発者ガイド&#40;分析サービス&#41;](analysis-services-developer-documentation.md)   
 [SQL Server リソース センター](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
