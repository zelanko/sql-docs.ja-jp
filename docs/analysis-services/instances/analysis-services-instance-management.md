---
title: SQL Server Analysis Services サーバーの管理 |Microsoft Docs
ms.date: 11/15/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a93a7ddb0af87ae15f8d793f21a008d9a4bc25c
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579072"
---
# <a name="sql-server-analysis-services-server-management"></a>SQL Server Analysis Services サーバーの管理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Azure Analysis Services では、次を参照してください。 [Azure Analysis Services の管理](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage)します。

## <a name="instances"></a>インスタンス

  Analysis Services のサーバー インスタンスのコピーである、 **msmdsrv.exe**オペレーティング システム サービスとして実行される実行可能ファイルです。 各インスタンスは同じサーバー上の他のインスタンスから完全に独立しており、固有の構成設定、権限、ポート、開始アカウント、ファイル ストレージ、およびサーバー モード プロパティを持ちます。  
  
 各インスタンスは、Windows サービスとして、Msmdsrv.exe、定義されているログオン アカウントのセキュリティ コンテキストで実行されます。  
  
-   既定のインスタンスのサービス名は MSSQLServerOLAPService です。  
  
-   各名前付きインスタンスのサービス名は、MSOLAP$ InstanceName です。  
  
> [!NOTE]  
>  セットアップが統合されているリダイレクター サービスもインストールされます複数のインスタンスがインストールされている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービス。 リダイレクター サービスは、クライアントを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の適切な名前付きインスタンスにリダイレクトします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは常に、ローカル サービス アカウントのセキュリティ コンテキストに従って実行されます。ローカル システム アカウントは、ローカル コンピューター外部のリソースにアクセスしないサービスを実行するために Windows で使用される制限付きのユーザー アカウントです。  
  
 複数インスタンスとは、同じハードウェアに複数のサーバー インスタンスをインストールしてスケールアップできることを意味します。 Analysis Services では、同じサーバー上に複数のインスタンスを置き、各インスタンスを特定のモードで実行するように構成することで、異なるサーバー モードをサポートできることも意味します。  

## <a name="server-mode"></a>サーバー モード
  
 サーバー モードは、そのインスタンスに使用するストレージおよびメモリ アーキテクチャを決定するサーバー プロパティです。 多次元モードで稼働するサーバーは、多次元キューブ データベースおよびデータ マイニング モデル用に構築されたリソース管理レイヤーを使用します。 これに対して、表形式サーバー モードでは、VertiPaq メモリ内分析エンジンとデータ圧縮を使用してデータを要求に応じて集計します。  
  
 ストレージ アーキテクチャとメモリ アーキテクチャの違いは、Analysis Services の単一インスタンスが表形式データベースと多次元データベースの両方ではなくどちらか一方で稼働することを意味します。 サーバー モード プロパティは、インスタンス上で実行されるデータベースの種類を決定します。  
  
 サーバー モードは、インストール時に、サーバーで実行されるデータベースの種類を指定するときに設定します。 使用可能なすべてのモードをサポートするには、Analysis Services の複数のインスタンスをインストールし、構築しているプロジェクトに対応するサーバー モードで各インスタンスを配置します。  
  
 原則として、実行する必要のある管理タスクの大部分はモードによって異なりません。 Analysis Services システム管理者は、インストール方法にかかわらず同じ手順とスクリプトを使用して、ネットワーク上で任意の Analysis Services インスタンスを管理できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint は例外です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の配置のサーバー管理は、常に SharePoint ファームのコンテキスト内で行われます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] は、常に単一インスタンスであり、常に SharePoint サーバーの全体管理または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用して管理されるという点が他のサーバー モードと異なります。 SQL Server Management Studio または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]for SharePoint に接続することもできますが、この操作は望ましくありません。 SharePoint ファームには、サーバーの状態を同期し、サーバーの可用性を監視するインフラストラクチャが含まれます。 他のツールを使用すると、これらの操作と競合する可能性があります。 詳細については[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サーバーの管理を参照してください[Power Pivot for SharePoint](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)します。  
  
  
  
## <a name="see-also"></a>関連項目  
 [テーブルと多次元ソリューションのソリューションの比較](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
