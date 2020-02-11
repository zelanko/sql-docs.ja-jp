---
title: データマイニングソリューションおよびオブジェクトの管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15574819cf0f0fec0d95fa2353c187cc55091e56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084201"
---
# <a name="management-of-data-mining-solutions-and-objects"></a>データ マイニング ソリューションおよびオブジェクトの管理
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、既存のマイニング構造とマイニング モデルの管理に使用できるクライアント ツールがあります。 ここでは、それぞれの環境を使用して実行できる管理操作について説明します。  
  
 これらのツールに加え、AMO や [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに接続する他のクライアント (たとえば [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドイン) を使用することで、プログラムでデータ マイニング オブジェクトを管理できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ マイニング オブジェクトの移動](moving-data-mining-objects.md)  
  
 [データマイニング&#41;&#40;処理の要件と考慮事項](processing-requirements-and-considerations-data-mining.md)  
  
 [SQL Server プロファイラーを使用したデータマイニングの監視 &#40;Analysis Services-データマイニング&#41;](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a>データ マイニング オブジェクトの場所  
 処理されたマイニング構造およびマイニング モデルは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されます。  
  
 データマイニングオブジェクトの開発時に[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]モードで`Immediate`データベースへの接続を作成すると、作成したオブジェクトは、作業中にサーバーにすぐに追加されます。 一方、 **の既定の動作である** オフライン [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モードでデータ マイニング オブジェクトを設計した場合、作成したマイニング オブジェクトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置されるまでは単なるメタデータ コンテナーです。 そのため、オブジェクトに変更を加えた場合は、オブジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに再配置する必要があります。 データ マイニングのアーキテクチャの詳細については、「[物理アーキテクチャ (Analysis Services - データ マイニング)](physical-architecture-analysis-services-data-mining.md)」を参照してください。  
  
> [!NOTE]  
>  
  [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドインなどの一部のクライアントでは、インスタンスへの接続を使用する一方でマイニング構造およびマイニング モデルをセッション中のみサーバー上に格納する、セッション マイニング モデルおよびセッション マイニング構造を作成することもできます。 これらのモデルは、クライアントを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに格納されている構造およびモデルの場合と同じ方法で管理できますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスとの接続を解除したときにオブジェクトは保持されません。  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a>SQL Server データ ツールでのデータ マイニング オブジェクトの管理  
 
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、データ マイニング オブジェクトの作成、参照、および編集を容易にする機能が用意されています。  
  
 次のリンクでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用してデータ マイニング オブジェクトを変更する方法について説明しています。  
  
-   [マイニング構造に使用されるデータ ソース ビューの編集](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [マイニング構造のプロパティの変更](change-the-properties-of-a-mining-structure.md)  
  
-   [マイニング モデルのプロパティの変更](change-the-properties-of-a-mining-model.md)  
  
-   [データマイニング&#41;&#40;モデリングフラグを表示または変更する](modeling-flags-data-mining.md)  
  
-   [アルゴリズム パラメーターの表示または変更](view-or-change-algorithm-parameters.md)  
  
 通常は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をツールとして使用して、新しいプロジェクトの開発と既存のプロジェクトへの追加を行い、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]などのツールを使用して配置されたプロジェクトとオブジェクトを管理します。  
  
 ただし、`Immediate` オプションを使用し、オンライン モードでサーバーに接続することで、ssASnoversion のインスタンスに既に配置されているオブジェクトを直接変更できます。 詳細については、「 [Analysis Services データベースへのオンライン モードでの接続](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)」を参照してください。  
  
> [!WARNING]  
>  名前や説明などのメタデータの変更を含め、マイニング構造またはマイニング モデルに対して変更を加えた場合は、構造またはモデルを再処理する必要があります。  
  
 データ マイニング プロジェクトまたはオブジェクトの作成に使用したソリューション ファイルがない場合は、Analysis Services のインポート ウィザードを使用してサーバーから既存のプロジェクトをインポートし、オブジェクトに変更を加え、`Incremental` オプションを使用して再配置できます。 詳細については、「 [Analysis Services インポート ウィザードを使用したデータ マイニング プロジェクトのインポート](import-a-data-mining-project-using-the-analysis-services-import-wizard.md)」を参照してください。  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a>SQL Server Management Studio でのデータ マイニング オブジェクトの管理  
 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、マイニング構造とマイニング モデルのスクリプト処理、処理、または削除を行うことができます。 オブジェクト エクスプローラーを使用した場合はプロパティ セットの一部のみが表示されます。ただし、 **[DMX クエリ]** ウィンドウを開き、マイニング構造を選択すると、マイニング モデルに関する追加のメタデータを表示できます。  
  
-   [SQL Server Management Studio で DMX クエリを作成する](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a>データ マイニング オブジェクトのプログラムによる管理  
 次のプログラミング言語を使用すると、データ マイニング オブジェクトの作成、変更、処理、および削除の操作を行うことができます。 各言語は別々のタスクを対象として設計されています。結果として、実行できる操作の種類に制限があります。 たとえば、データ マイニング オブジェクトの一部のプロパティはデータ マイニング拡張機能 (DMX) では変更できず、XMLA または AMO を使用する必要があります。  
  
### <a name="analysis-management-objects-amo"></a>分析管理オブジェクト (AMO)  
 分析管理オブジェクト (AMO) は、データ マイニング オブジェクトを完全に制御できる、XMLA に基づいて構築されたオブジェクト モデルです。 AMO を使用して、マイニング構造とマイニング モデルを作成、配置、および監視できます。  
  
-   [AMO の概念とオブジェクト モデル](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **制限:** 存在.  
  
### <a name="data-mining-extensions-dmx"></a>データ マイニング拡張機能 (DMX)  
 データ マイニング拡張機能 (DMX) は、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] や ADOMD.Net などの他のコマンド インターフェイスと組み合わせて、マイニング構造とマイニング モデルを作成、削除、およびクエリできます。  
  
-   [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](/sql/dmx/dmx-statements-data-definition)  
  
 **制限:** 一部のプロパティは、DMX を使用して変更することはできません。  
  
### <a name="xml-for-analysis-xmla"></a>XML for Analysis (XMLA)  
 XML for Analysis (XMLA) は、すべての Analysis Services 用のデータ定義言語です。 XMLA を使用して、ほとんどのデータ マイニング オブジェクトとサーバーの動作を制御できます。 XMLA を使用すると、クライアントとサーバーの間で行うすべての管理操作を実行できます。 便宜上、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) を使用して XML をラップできます。  
  
 **制限事項:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内部使用のみがサポートされ、XML DDL スクリプトでは使用できない XMLA ステートメントが生成されます。  
  
## <a name="see-also"></a>参照  
 [開発者ガイド &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)  
  
  
