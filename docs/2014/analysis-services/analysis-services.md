---
title: Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: b18efaacb7ab891402e84b851735870c4c47e883
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360514"
---
# <a name="analysis-services"></a>Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、意思決定支援とビジネス インテリジェンス (BI) ソリューションに使用されるオンライン分析データ エンジンであり、ビジネス レポートおよび、Excel、Reporting Services レポート、他のサード パーティの BI ツールのようなクライアント アプリケーションによって使用される分析データを提供します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の一般的なワークフローには、OLAP または表形式のデータ モデルを作成し、そのモデルをデータベースとして [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに配置し、データが読み込まれるようにデータベースを処理し、データへのアクセスを許可する権限を割り当てることが含まれます。 準備が完了すると、複数の用途を持つこのデータ モデルに、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をデータ ソースとしてサポートしている任意のクライアント アプリケーションがアクセスできるようになります。  
  
 モデルを作成するには、SQL Server Data Tools を使用 (を参照してください[ツールと Analysis Services で使用されるアプリケーション](tools-and-applications-used-in-analysis-services.md))、いずれかを表形式または多次元およびデータ マイニング プロジェクト テンプレートを選択します。 プロジェクト テンプレートには、モデルで必要とされるすべてのオブジェクトのフォルダーが含まれています。 ウィザードを使用して、データ ソース、データ ソース ビュー、ディメンション、キューブ、ロールなど、すべての基本的な要素を作成することができます。  
  
 モデルは、外部データ システムから取得したデータによって作成されます。通常は外部データ システムとして、SQL Server または Oracle リレーショナル データベース エンジンでホストされているデータ ウェアハウスを使用します (テーブル モデルでは、追加のデータ ソースの種類もサポートされています)。 モデルは、キューブなどのクエリ オブジェクトを指定しますが、複数のキューブ、計算、KPI (ビジネス ロジック、ナビゲーションやドリルスルー動作などの相互作用をカプセル化する) で使用できるディメンションも指定します。  
  
 このモデルを使用するために、モデルを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに配置します。このインスタンスは特定のサーバー モードでデータベースを実行し、Excel または他のアプリケーションから接続する認証済みユーザーがデータを使用できるようにします。  
  
 次の 3 つのサーバー モードのいずれかで、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスをインストールできます。  
  
-   テーブル インスタンスとしてインストールし、テーブル モデルを実行します。  
  
-   多次元およびデータ マイニングのインスタンスとしてインストールし、OLAP キューブとデータ マイニング モデルを実行します (既定)。  
  
-   PowerPivot for SharePoint としてインストールし、SharePoint 上で PowerPivot と Excel データ モデルを実行します (PowerPivot for SharePoint は中間層のデータ エンジンであり、SharePoint でホストされているデータ モデルの読み込み、クエリ、更新を実行します)。  
  
 同じデータ エンジンを、3 つの方法で使用できます。 サーバー モードはインストール中に設定され、後で変更できないことに注意してください。 別のモードが必要な場合は、新しいインスタンスをインストールする必要があります。  
  
 Analysis Services に関する基本ドキュメントは、作成するプロジェクトの種類に対応するセクション別に分類されます。 それぞれのモードまたは機能領域の詳細については、次のリンクから選択してください。  
  
 **領域ごとのコンテンツの参照**  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テーブルと多次元ソリューションのソリューションの比較&#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [Analysis Services インスタンスの管理](instances/analysis-services-instance-management.md)  
  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テーブル モデリング&#40;SSAS 表形式&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[多次元モデリング&#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[データ マイニング&#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能は、エディションによって異なります。 多次元およびデータ マイニング モデルは Standard Edition で使用できますが、上位エディションに比べると機能が少なくなっています。 テーブル モデルと PowerPivot for SharePoint はプレミアム機能であり、Standard Edition のライセンスでは使用できません。 詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services チュートリアル&#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [SQL Server 2014 のインストール](../database-engine/install-windows/installation-for-sql-server.md)   
 [Developer's Guide &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [SQL Server リソース センター](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
