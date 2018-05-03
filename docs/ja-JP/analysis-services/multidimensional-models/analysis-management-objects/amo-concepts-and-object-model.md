---
title: AMO の概念とオブジェクト モデル |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 778007f9cdf5b2c0eea94d9d202545e95476d1c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="amo-concepts-and-object-model"></a>AMO の概念とオブジェクト モデル
  このトピックは、分析管理オブジェクト (AMO) の定義を提供 AMO が他のツールとのアーキテクチャで提供されるライブラリに関連するどの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]AMO 内のすべての主要なオブジェクトの概念について説明します。  
  
 AMO は、マネージ環境において、<xref:Microsoft.AnalysisServices> の名前空間のプログラムで使用できる、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の管理クラスの完全なコレクションです。 クラスは、where が通常見つかる AnalysisServices.dll ファイルに含まれる、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フォルダー \100\SDK\Assemblies 下で、ファイルがインストール\\です。 AMO クラスを使用するには、このアセンブリへの参照をプロジェクト内に含めてください。  
  
 作成することができる AMO を使用すると、変更、およびキューブ、ディメンション、マイニング構造などのオブジェクトを削除し、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース; に対してこれらすべてのオブジェクト、.NET Framework のアプリケーションから、操作を実行できます。 また、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースに格納された情報を処理したり、更新したりできます。  
  
 AMO を使用して、データに対するクエリを実行することはできません。 クエリを実行する、データを使用して[ADOMD.NET での開発](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)です。  
  
 このトピックには、次のセクションが含まれます。  
  
 [Analysis Services のアーキテクチャの AMO](#AMOintheAnalysisServicesArchitecture)  
  
 [AMO のアーキテクチャ](#AMOArchitecture)  
  
 [AMO を使用してください。](#bkmk_UsingAMO)  
  
 [AMO による管理タスクを自動化します。](#AutomatingAdministrativeTaskswithAMO)  
  
##  <a name="AMOintheAnalysisServicesArchitecture"></a> Analysis Services のアーキテクチャの AMO  
 AMO はオブジェクト管理のみを用途として設計されており、データのクエリは用途外です。 ユーザーが必要な場合のクエリ[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]クライアント アプリケーションからデータをクライアント アプリケーションで使用する必要があります[ADOMD.NET での開発](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)です。  
  
##  <a name="AMOArchitecture"></a> AMO のアーキテクチャ  
 AMO のインスタンスを管理するためのクラスの完全なライブラリ[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]は .NET Framework version 2.0 でマネージ コードでクライアント アプリケーションからです。  
  
 AMO クラス ライブラリの設計上、クラス間に階層関係があり、コードを記述する際、一部のクラスをインスタンス化してからその他のクラスを使用する必要があります。 また、コード内でいつでもインスタンス化できる補助クラスもあります。ただし、多くの場合、いずれかの補助クラスを使用する前に、1 つ以上の階層クラスが既にインスタンス化されています。  
  
 次の図は、主要なクラスを含む AMO 階層の概要を示しています。 この図では、各クラスがそのコンテナーとピアの間に配置されています。 <xref:Microsoft.AnalysisServices.Dimension> は <xref:Microsoft.AnalysisServices.Database> および <xref:Microsoft.AnalysisServices.Server> に属し、<xref:Microsoft.AnalysisServices.DataSource> および <xref:Microsoft.AnalysisServices.MiningStructure> と同時に作成できます。 他のクラスを使用するには、特定のピア クラスをインスタンス化する必要があります。 たとえば、新規に <xref:Microsoft.AnalysisServices.DataSource> または <xref:Microsoft.AnalysisServices.Dimension> を追加する前に、<xref:Microsoft.AnalysisServices.MiningStructure> のインスタンスを作成する必要があります。  
  
 ![AMO クラスの上位レベル ビュー](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-highlevelview-majorobjectshighlighted.gif "AMO クラスの上位レベル ビュー")  
  
 A*の主要なオブジェクト*エンティティ全体とは別のオブジェクトの一部ではなく、完全なオブジェクトを表すクラスです。 主要オブジェクトには、<xref:Microsoft.AnalysisServices.Server>、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.MiningStructure> が含まれます。これらはいずれも独立したエンティティです。 しかし、<xref:Microsoft.AnalysisServices.Level> は <xref:Microsoft.AnalysisServices.Dimension> の構成要素なので、主要オブジェクトではありません。 主要オブジェクトは、他のオブジェクトに関係なく、作成、削除、変更、または処理できます。 副次オブジェクトは、親である主要オブジェクトを作成する際に、その一部としてのみ作成できるオブジェクトです。 通常、副次オブジェクトは、主要オブジェクトの作成時に作成されます。 副次オブジェクトの値は作成時に定義してください。副次オブジェクトには既定値が作成されないためです。  
  
 次の図は、<xref:Microsoft.AnalysisServices.Server> オブジェクトに含まれる主要なオブジェクトを示しています。  
  
 ![強調表示された AMO の主なオブジェクト](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects.gif "強調表示された AMO の主なオブジェクト")  
  
 ![(2) が強調表示された AMO の主なオブジェクト](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects-02.gif "(2) が強調表示された AMO の主なオブジェクト")  
  
 AMO を使用してプログラミングする場合、クラスと、含まれているクラスの関連付けには、コレクションの種類の属性 (<xref:Microsoft.AnalysisServices.Server> や <xref:Microsoft.AnalysisServices.Dimension> など) を使用します。 含まれているクラスのインスタンスを使用するには、まず、そのクラスが含まれているか、含まれている可能性のあるコレクション オブジェクトへの参照を取得します。 次に、必要とするオブジェクトをコレクション内で特定し、オブジェクトへの参照を取得すれば、これを使用できるようになります。  
  
### <a name="amo-classes"></a>AMO クラス  
 AMO は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスをクライアント アプリケーションから管理するよう設計されたクラスのライブラリです。 AMO ライブラリは、特定のタスクの実行に使用される、論理的に関連したオブジェクトのグループとして考えることができます。 AMO クラスは、次のように分類できます。  
  
|クラス セット|用途|  
|---------------|-------------|  
|[AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)|他のクラスのセットを操作するために必須のクラス。|  
|[AMO OLAP クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で OLAP オブジェクトを管理するためのクラス。|  
|[AMO データ マイニング クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でデータ マイニング オブジェクトの管理を可能にするためのクラス。|  
|[AMO セキュリティ クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-security-classes.md)|他のオブジェクトへのアクセスを制御し、セキュリティのメンテナンスを可能にするためのクラス。|  
|[AMO のその他のクラスとメソッド](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)|OLAP またはデータ マイニングの管理者の日常的業務の遂行に役立つ、クラスおよびメソッド。|  
  
##  <a name="bkmk_UsingAMO"></a> AMO を使用してください。  
 AMO は、繰り返しタスクの自動化に非常に役立ちます。たとえば、ファクト テーブルの新しいデータに基づいてメジャー グループに新しいパーティションを作成する場合や、新しいデータに基づいてマイニング モデルを再調整する場合などです。 新しいオブジェクトを作成するこれらのタスクは、通常、毎月、毎週、または四半期ごとに実行され、アプリケーションで新しいオブジェクトに新しいデータに基づく名前を付けることも簡単です。  
  
##### <a name="analysis-services-administrators"></a>Analysis Services 管理者  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理者は、AMO を使用して、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースの処理を自動化できます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースの設計および配置には、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] を使用してください。  
  
##### <a name="developers"></a>開発者  
 開発者は、AMO を使用して、指定したユーザー セット用の管理インターフェイスを開発できます。 これらのインターフェイスでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトへのアクセスを制限し、ユーザーが特定のタスクのみを使用できるようにできます。 たとえば、AMO を使用すると、すべてのデータベース オブジェクトの表示、データベースのいずれかの選択、および指定したデバイス セットのいずれかのデバイスへのバックアップをユーザーに許可する、バックアップ アプリケーションを作成できます。  
  
 開発者はまた、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ロジックをアプリケーションに埋め込むことができます。 このため、開発者は、ユーザー入力などの要因に基づいて、キューブ、ディメンション、マイニング構造、およびマイニング モデルを作成できます。  
  
##### <a name="olap-advanced-users"></a>OLAP の上級ユーザー  
 データ アナリストや経験豊富なデータ ユーザーをはじめとする OLAP の上級ユーザーは、プログラミングに関する豊富な背景知識を持ち、データ オブジェクトをさらに緻密に使用してデータ分析を強化したいと望んでいます。 オフライン作業が必要なユーザーにとって、オフラインへの切り替え前のローカル キューブの作成を自動化するために、AMO が非常に役立ちます。  
  
##### <a name="data-mining-advanced-users"></a>データ マイニングの上級ユーザー  
 データ マイニングの上級ユーザーにとって、定期的な再調整を必要とするモデル セットが大量にある場合に、AMO が非常に役立ちます。  
  
##  <a name="AutomatingAdministrativeTaskswithAMO"></a> AMO による管理タスクを自動化します。  
 ほとんどの繰り返しタスクは、どのような言語のアプリケーションとして開発するよりも [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] を使用して開発した方が、設計、配置、および保守に適しています。 しかし、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] を使用しても自動化できない繰り返しタスクには、AMO を使用できます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] を使用して、ビジネス インテリジェンス用に専門性の高いアプリケーションを開発する際にも、AMO が役立ちます。  
  
##### <a name="automatic-object-management"></a>自動オブジェクト管理  
 AMO を使用すると、ユーザー入力や新しく取得したデータに基づいて、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクト (<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.MiningStructure>、<xref:Microsoft.AnalysisServices.MiningModel>、<xref:Microsoft.AnalysisServices.Role> など) を容易に作成、更新、または削除できます。 AMO は、独立系ソフトウェア ベンダーによって開発されたソリューションを、最終的な顧客に配置するためのセットアップ アプリケーションに最適です。 セットアップ アプリケーションでは、旧バージョンが存在するかどうかを検証し、構造を更新し、不要なオブジェクトを削除し、新しいオブジェクトを作成できます。 旧バージョンが存在しない場合は、すべてを最初から作成します。  
  
 AMO は、新しいデータに基づく新しいパーティションの作成に威力を発揮します。また、プロジェクトのスコープから外れた古いパーティションを削除することもできます。 たとえば、過去 36 か月のデータを使用する財務分析ソリューションでは、新しい月のデータが入力されしだい、37 番目の月のデータが削除されるようにできます。 パフォーマンスを最適化するためには、使用率に基づく集計を新しく設計し、過去 12 か月分に適用できます。  
  
##### <a name="automatic-object-processing"></a>自動オブジェクト処理  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] を使用する通常のフロー データや定期タスク以外の、特定のイベントに応答するように AMO を使用すると、オブジェクト処理や可用性の更新が可能です。  
  
##### <a name="automatic-security-management"></a>自動セキュリティ管理  
 セキュリティ管理を自動化して、新しいユーザーをロールや権限に含めたり、時間切れになったユーザーを削除したりできます。 新しいインターフェイスを作成して、セキュリティ管理者によるセキュリティ管理を単純化できます。 これは、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] を使用するよりも簡単です。  
  
##### <a name="automatic-backup-management"></a>自動バックアップ管理  
 自動バックアップ管理を行うには、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] タスクを使用するか、自動実行される特別な AMO アプリケーションを作成します。 AMO を使用すると、オペレーターの日常業務を支援するバックアップ インターフェイスを開発できます。  
  
##### <a name="tasks-amo-is-not-intended-for"></a>AMO を使用しないタスク  
 データのクエリには、AMO を使用できません。 キューブやマイニング モデルなどの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データにクエリを実行するには、ユーザー アプリケーションから ADOMD.NET を使用してください。 詳細については、次を参照してください。 [ADOMD.NET での開発](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)です。  
  
  
