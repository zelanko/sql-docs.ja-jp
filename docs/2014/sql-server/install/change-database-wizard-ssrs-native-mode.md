---
title: データベースの変更ウィザード (SSRS ネイティブ モード) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 256d91789d4bc1413580fde6f5c40ff8151f309a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084220"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>データベースの変更ウィザード (SSRS ネイティブ モード)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager が、データベースの変更ウィザードを使用する新しいレポート サーバー データベースを作成するか、現在のレポート サーバー インスタンスで使用する既存のレポート サーバー データベースを選択すると次の手順を提供します。  
  
 以前のバージョンのレポート サーバー データベースを選択すると、接続先のレポート サーバー インスタンスのバージョンと一致するようにアップグレードされます。 サービスの開始時にデータベース バージョンが確認され、現在のスキーマに自動的にアップグレードされます。  
  
 クリックして、ウィザードを起動する**データベースの変更**データベース ページで、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager です。 開始する方法については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成マネージャーを参照してください[Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)です。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
## <a name="options"></a>および  
 **操作**  
 実行するタスクを選択します。 ネイティブ モードまたは SharePoint 統合モードで新しいデータベースを作成できます。 または、現在のレポート サーバー インスタンスで使用する既存のレポート サーバー データベースを選択できます。  
  
 **データベース サーバー**  
 名前を指定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]レポート サーバー データベースをホストするインスタンス。 ローカルまたはリモートのコンピューターの、既定または名前付きのインスタンスを使用できます。 名前付きインスタンスに接続する場合は、この形式でサーバー名を入力: \<*サーバー*>\\<*インスタンス*>。  
  
 接続する、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンス、データベース情報を更新したりサーバーにログオンする権限を持つ資格情報を使用する必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager が、現在の Windows 資格情報を使用しますが、ログインまたはデータベースのアクセス許可がないを指定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ログインします。 別の Windows 資格情報を指定することはできません。 別の Windows ユーザー、そのユーザーとしてログインとして接続してから開始する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager です。  
  
 リモート インスタンスに接続する場合は、まずそのインスタンスでリモート接続を有効にする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよびエディションの中には、既定でリモート接続が有効になっていないものもあります。 リモート接続が許可されているかどうかを確認するを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager と、TCP/IP および名前付きパイプ プロトコルが有効になっていることを確認します。 リモート インスタンスが名前付きインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが有効になっていることと、対象サーバーで実行されていることを確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ブラウザーに名前付きインスタンスによって使用されるポート番号を提供する、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager です。  
  
 **[データベース]**  
 サーバー データを格納するレポート サーバー データベースの名前を指定します。 既存のデータベースを指定するか、新しいデータベースを作成できます。  
  
 [アクション] ページで **[新しいデータベースを作成する]** を選択すると、新しいデータベースの作成に使用されるプロパティがウィザードに表示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager は、名前でバインドされている 2 つのデータベースを作成します。 静的データとセッションおよび作業データを格納するための一時データベースに格納するデータベース。 詳細については、次を参照してください。[レポート サーバー データベース&#40;SSRS ネイティブ モード&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブック。  
  
 既存のレポート サーバー データベースを選択することもできます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは、無効なデータベースが除外されません。 有効なデータベースは、レポート サーバー データベース スキーマに基づきます (必要なテーブル、ビュー、またはストアド プロシージャが欠落しているデータベースは選択できません)。 以前のバージョンの用に作成されたデータベースを選択するかどうかは[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]データベースは、現在の形式にアップグレードされます。  
  
 **言語**  
 この値は、新しいレポート サーバー データベースを作成する場合にのみ設定します。  
  
 この値を使用して、ロールの定義および説明を作成するときの言語を指定します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、一連の定義済みロールを含んでいるロールベースの承認モデルが用意されています。 ロールは、指定した言語で一度だけ作成されます。 サーバーでサポートされているカルチャまたは言語が設定されているブラウザーを使用してレポート サーバーに接続した場合でも、ロール名と説明が指定以外の言語で表示されることはありません。 また、指定した言語によって、個人用レポート機能に含まれている [個人用レポート] フォルダーおよび [Users] フォルダーの名前の作成に使用される言語も決定されます。  
  
 **サーバー モード**  
 レポート サーバー データベースでは、ネイティブ モードまたは SharePoint 統合モードのいずれかがサポートされます。 これらのモードは、同時には指定できません。  
  
 新しいレポート サーバー データベースを作成する場合は、モードを指定する必要があります。 選択したモード、レポート サーバー データベースとセットの構造を決定する、`SharePointIntegrated`レポート サーバー システム プロパティを`true`または`false`です。  
  
 別のレポート サーバー データベースを選択する場合は、現在のデータベースの使用方法がわかるように、現在のデータベースのモードが表示されます。  
  
 **資格情報**  
 レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを指定します。 有効な値は、レポート サーバー Web サービスのサービス アカウント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で定義されているデータベース ログイン、[!INCLUDE[ssDE](../../includes/ssde-md.md)]レポート サーバーまたは Windows アカウントをホストしているインスタンス。 Windows アカウントを使用している場合は、ローカル アカウントを指定することができます (*\<computername >\\< ユーザー名\>*) 場合は、レポート サーバーとデータベースが、同じコンピューターまたはドメイン ユーザーにはアカウント (*\<ドメイン >\\< ユーザー名\>*)、同じドメイン内の異なるコンピューターにある場合。  
  
 レポート サーバーはデータベース ログインを作成し、指定したアカウントにデータベース権限を割り当てます。  
  
 レポート サーバーでは、アカウントの作成は行われません。 配置構成に対して有効な、既に存在するアカウントを指定する必要があります。 特に、データベースがリモート コンピューター上にある環境で、Windows アカウントを使用する場合は、そのコンピューターへのログオン権限のあるアカウントを指定する必要があります。  
  
 コンピューターが異なるまたは信頼されていないドメイン内にある場合は、使用を検討して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ログインします。 アカウントの選択の詳細については、次を参照してください。[レポート サーバー データベース接続を構成する&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)です。  
  
 **概要**  
 セットアップで接続を構成する前に、設定を確認します。  
  
 **進行状況と完了**  
 各タスクの進行状況を監視します。  
  
## <a name="see-also"></a>参照  
 [データベース&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [変更の資格情報ウィザード&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [レポート サーバー データベース接続を構成する&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  