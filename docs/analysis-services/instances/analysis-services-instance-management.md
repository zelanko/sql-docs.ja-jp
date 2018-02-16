---
title: "Analysis Services インスタンスの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0455fa4f-b92d-4a8b-a8f0-f2a268a5c84e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1540e9a5422b3a15081b1a25c813ef87ed8d6c0c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="analysis-services-instance-management"></a>Analysis Services インスタンス管理

  Analysis Services のインスタンスは、オペレーティング システム サービスとして実行される **msmdsrv.exe** 実行可能ファイルのコピーです。 各インスタンスは同じサーバー上の他のインスタンスから完全に独立しており、固有の構成設定、権限、ポート、開始アカウント、ファイル ストレージ、およびサーバー モード プロパティを持ちます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の各インスタンスは、定義されているログオン アカウントのセキュリティ コンテキストに従い、Msmdsrv.exe という Windows サービスとして実行されます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のインスタンスのサービス名は MSSQLServerOLAPService です。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の各名前付きインスタンスのサービス名は MSOLAP$InstanceName です。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスが複数インストールされている場合は、セットアップによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスに統合されているリダイレクター サービスもインストールされます。 リダイレクター サービスは、クライアントを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の適切な名前付きインスタンスにリダイレクトします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは常に、ローカル サービス アカウントのセキュリティ コンテキストに従って実行されます。ローカル システム アカウントは、ローカル コンピューター外部のリソースにアクセスしないサービスを実行するために Windows で使用される制限付きのユーザー アカウントです。  
  
 複数インスタンスとは、同じハードウェアに複数のサーバー インスタンスをインストールしてスケールアップできることを意味します。 Analysis Services では、同じサーバー上に複数のインスタンスを置き、各インスタンスを特定のモードで実行するように構成することで、異なるサーバー モードをサポートできることも意味します。  
  
 サーバー モードは、そのインスタンスに使用するストレージおよびメモリ アーキテクチャを決定するサーバー プロパティです。 多次元モードで稼働するサーバーは、多次元キューブ データベースおよびデータ マイニング モデル用に構築されたリソース管理レイヤーを使用します。 これに対して、表形式サーバー モードでは、VertiPaq メモリ内分析エンジンとデータ圧縮を使用してデータを要求に応じて集計します。  
  
 ストレージ アーキテクチャとメモリ アーキテクチャの違いは、Analysis Services の単一インスタンスが表形式データベースと多次元データベースの両方ではなくどちらか一方で稼働することを意味します。 サーバー モード プロパティは、インスタンス上で実行されるデータベースの種類を決定します。  
  
 サーバー モードは、インストール時に、サーバーで実行されるデータベースの種類を指定するときに設定します。 使用可能なすべてのモードをサポートするには、Analysis Services の複数のインスタンスをインストールし、構築しているプロジェクトに対応するサーバー モードで各インスタンスを配置します。  
  
 原則として、実行する必要のある管理タスクの大部分はモードによって異なりません。 Analysis Services システム管理者は、インストール方法にかかわらず同じ手順とスクリプトを使用して、ネットワーク上で任意の Analysis Services インスタンスを管理できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint は例外です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の配置のサーバー管理は、常に SharePoint ファームのコンテキスト内で行われます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] は、常に単一インスタンスであり、常に SharePoint サーバーの全体管理または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用して管理されるという点が他のサーバー モードと異なります。 SQL Server Management Studio または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]for SharePoint に接続することもできますが、この操作は望ましくありません。 SharePoint ファームには、サーバーの状態を同期し、サーバーの可用性を監視するインフラストラクチャが含まれます。 他のツールを使用すると、これらの操作と競合する可能性があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー管理の詳細については、「[Power Pivot for SharePoint (SSAS)](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|リンク|タスクの説明|  
|----------|----------------------|  
|[インストール後の構成 &#40;です。Analysis Services &#41;](../../analysis-services/instances/post-install-configuration-analysis-services.md)|Analysis Services のインストールを完了または変更する必須のタスクとオプションのタスクについて説明します。|  
|[Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)|接続を確立またはクリアするための接続文字列プロパティ、クライアント ライブラリ、認証方法、および手順について説明します。|  
|[Analysis Services インスタンスを監視します。](../../analysis-services/instances/monitor-an-analysis-services-instance.md)|パフォーマンス モニターと SQL Server Profiler の使用方法など、サーバー インスタンスの監視のためのツールと手法について説明します。|  
|[高可用性とスケーラビリティ](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)|Analysis Services データベースの高可用性とスケーラビリティを確保するために最もよく使用される手法について説明します。 |  
|[Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)|言語と照合順序のサポート、両方のプロパティの変更手順、および言語と照合順序の動作の設定とテストのヒントについて説明します。|  
|[Analysis Services でのログ操作](../../analysis-services/instances/log-operations-in-analysis-services.md)|ログについて説明し、その構成方法について解説します。|  
  
  
## <a name="see-also"></a>参照  
 [テーブル ソリューションと多次元ソリューションの比較 (SSAS)](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Power Pivot Configuration Tools](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
