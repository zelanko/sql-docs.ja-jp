---
title: "カスタム ワークフロー (Master Data Services) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8e4403e9-595c-4b6b-9d0c-f6ae1b2bc99d
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dacc515af7f4d05fc2bad2fd43535bc27c13ea76
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow-master-data-services"></a>カスタム ワークフローの作成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] は、ビジネス ルールを使用して基本的なワークフロー ソリューションを作成します (たとえば、指定した条件に基づいてデータを自動的に更新および検証し、電子メール通知を送信するなど)。 組み込みのワークフロー アクションよりも複雑な処理が必要な場合は、カスタム ワークフローを使用します。 カスタム ワークフローは、ユーザーが作成する .NET アセンブリです。 作成したワークフロー アセンブリが呼び出された際には、記述したコードを通じて、状況に応じた任意のアクションを実行できます。 たとえば、複数階層の承認や複雑な意思決定ツリーなど、複雑なイベント処理を必要とするワークフローの場合は、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を構成することで、データを分析し、データの承認のための送信先を決定するカスタム ワークフローを開始できます。  
  
## <a name="how-custom-workflows-are-processed"></a>カスタム ワークフローの処理方法  
 カスタム ワークフローの処理には、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、SQL Server MDS Workflow Integration Service、およびワークフロー ハンドラー アセンブリの 3 つの主要コンポーネントが関与します。 これらのコンポーネントは、カスタム ワークフローを次のように処理します。  
  
1.  ユーザーが [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用して、ワークフローを開始するエンティティを検証します。  
  
2.  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] は、ビジネス ルール条件を満たすメンバーを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース内の Service Broker キューに送ります。  
  
3.  SQL Server MDS Workflow Integration Service は、一定の間隔で [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース内のストアド プロシージャを呼び出します。  
  
4.  このストアド プロシージャは、Service Broker キュー内にレコードを見つけると、それらを SQL Server MDS Workflow Integration Service に返します。  
  
5.  SQL Server MDS Workflow Integration Services は、それらのデータをワークフロー ハンドラー アセンブリにルーティングします。  
  
> [!NOTE]  
>  注: SQL Server MDS Workflow Integration Service は単純な処理をトリガーするためのものです。 カスタム コードで複雑な処理を行う必要がある場合は、個別のスレッド内か、またはワークフロー プロセスの外部で処理を完了してください。  
  
## <a name="configure-master-data-services-for-custom-workflows"></a>カスタム ワークフロー向けの Master Data Services の構成  
 カスタム ワークフローを作成するには、カスタム コードの記述と [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] の構成を行って、ワークフロー データをワークフロー ハンドラーに渡す必要があります。 カスタム ワークフロー処理を有効にするには、次の手順を実行します。  
  
1.  <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender> を実装する .NET アセンブリ作成します。  
  
2.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに接続してワークフロー ハンドラーにタグを関連付けるよう、SQL Server MDS Workflow Integration Services を構成します。  
  
3.  SQL Server MDS Workflow Integration Service を開始します。  
  
4.  ワークフロー ハンドラーの名前でタグ付けされたワークフローを開始する [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 内で、ビジネス ルールを作成します。  
  
5.  そのビジネス ルールを、カスタム ワークフローをトリガーするメンバーに適用します。  
  
### <a name="create-the-workflow-handler-assembly"></a>ワークフロー ハンドラー アセンブリの作成  
 カスタム ワークフローは、<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender> インターフェイスを実装する .NET クラス ライブラリ アセンブリです。 SQL Server MDS Workflow Integration Service は、<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> メソッドを呼び出してコードを実行します。 実装するコード例<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>を参照してください[カスタム ワークフローの例 & #40 です。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 カスタム ワークフローを処理するために SQL Server MDS Workflow Integration Service から呼び出すことができるアセンブリを、Visual Studio 2010 を使用して作成するには、次の手順を実行します。  
  
1.  Visual Studio 2010 で作成、新しい**クラス ライブラリ**を任意の言語を使用するプロジェクトです。 C# クラス ライブラリを作成するには、選択、 **Visual C# \Windows**プロジェクトの種類を選択、**クラス ライブラリ**テンプレート。 など、プロジェクト名を入力**MDSWorkflowTest**、 をクリック**OK**です。  
  
2.  Microsoft.MasterDataServices.WorkflowTypeExtender.dll への参照を追加します。 このアセンブリは含まれて\<しインストール フォルダー > \Master Data Services\WebApplication\bin です。  
  
3.  C# コード ファイルに、'using Microsoft.MasterDataServices.Core.Workflow;' を追加します。  
  
4.  クラス宣言で、<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender> を継承します。 クラス宣言は次のようになります: 'public class WorkflowTester : IWorkflowTypeExtender'  
  
5.  実装、<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>インターフェイスです。 <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> メソッドは、ワークフローを開始するために SQL Server MDS Workflow Integration Service によって呼び出されます。  
  
6.  Microsoft.MasterDataServices.Workflow.exe をという名前で、SQL Server MDS Workflow Integration Service 実行可能ファイルの場所にアセンブリをコピー\<しインストール フォルダー > \Master Data Services\WebApplication\bin です。  
  
### <a name="configure-sql-server-mds-workflow-integration-service"></a>SQL Server MDS Workflow Integration Service の構成  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 構成ファイルを編集して、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース用の接続情報を含め、ワークフロー ハンドラー アセンブリにタグを関連付けるには、次の手順を実行します。  
  
1.  ある Microsoft.MasterDataServices.Workflow.exe.config を見つけます\<しインストール フォルダー > \Master Data Services\WebApplication\bin です。  
  
2.  "ConnectionString" 設定に、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース接続情報を追加します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールで大文字と小文字を区別する照合順序が使用されている場合、データベースの名前は、データベース内と同様の大文字/小文字で入力する必要があります。 たとえば、設定タグの全体は次のようになります。  
  
    ```xml  
    <setting name="ConnectionString" serializeAs="String">  
        <value>Server=myServer;Database=myDatabase;Integrated Security=True</value>  
    </setting>  
    ```  
  
3.  "ConnectionString" 設定下で "WorkflowTypeExtenders" 設定を追加して、ワークフロー ハンドラー アセンブリにタグ名を関連付けます。 例:  
  
    ```xml  
    <setting name="WorkflowTypeExtenders" serializeAs="String">  
        <value>TEST=MDSWorkflowTestLib.WorkflowTester, MDSWorkflowTestLib</value>  
    </setting>  
    ```  
  
     内部テキ スト、\<値 > の形式では、タグ\<ワークフロー タグ > =\<ワークフローのアセンブリ修飾型名 >。 \<ワークフロー タグ > でビジネス ルールを作成するときに、ワークフロー ハンドラー アセンブリの識別に使用する名前は、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]です。 \<ワークフローのアセンブリ修飾型名 > は、名前空間で修飾されたクラスの名前、ワークフロー、続いてコンマを続けて、アセンブリの表示名。 アセンブリに厳密な名前が指定されている場合は、バージョン情報と PublicKeyToken も含める必要があります。 複数を含めることができます\<設定 > タグを複数の異なる種類のワークフローのワークフロー ハンドラーを作成した場合。  
  
> [!NOTE]  
>  サーバーの構成によっては、Microsoft.MasterDataServices.Workflow.exe.config ファイルを保存する際に、"アクセスが拒否されました" というエラーが返されることがあります。 その場合は、サーバー上のユーザー アカウント制御 (UAC) を一時的に無効にしてください。 これを行うには、コントロール パネルを開き、**システムとセキュリティ**です。 **アクション センター**をクリックして**ユーザー アカウント制御設定の変更**です。 **ユーザー アカウント制御設定**ダイアログ ボックスで、スライダー バーを下部を合わせ、決して通知されるようにします。 コンピューターを再起動し、上記の手順を繰り返して、構成ファイルを編集します。 ファイルを保存したら、UAC 設定を既定のレベルにリセットしてください。  
  
### <a name="start-sql-server-mds-workflow-integration-service"></a>SQL Server MDS Workflow Integration Service の開始  
 既定では、SQL Server MDS Workflow Integration Service はインストールされていません。 使用する前に、まずこのサービスをインストールする必要があります。 最大限のセキュリティを確保するため、このサービス用のローカル ユーザーを作成し、そのユーザーに対して、ワークフロー操作の実行に必要な権限のみを付与してください。 ユーザーを作成し、サービスをインストールして、サービスを開始するには、次の手順を実行します。  
  
1.  [ローカル ユーザーとグループ] マネージャーを使用して、ローカル ユーザー (この例では mds_workflow_service) を作成します。  
  
2.  SQL Server Management Studio を使用して、mds_workflow_service ユーザーに、[mdm].[udpExternalActionsGet] ストアド プロシージャを実行する権限を付与します。 これを行うには、mds_workflow_service アカウント用の新規ログインを作成し、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース内に新規ユーザーを作成して、そのユーザーを mds_workflow_service ログインにマップした後、そのユーザーに、[mdm].[udpExternalActionsGet] ストアド プロシージャに対する EXECUTE 権限を付与します。  
  
3.  mds_workflow_service ユーザーに、ワークフロー ハンドラー アセンブリを実行する権限を付与します。 これを行うには、mds_workflow_service ユーザーを追加、**セキュリティ**のタブ、**プロパティ**ワークフロー ハンドラー アセンブリと、その mds_workflow_service ユーザー読み取りし、実行アクセス許可。  
  
4.  mds_workflow_service ユーザーに、SQL Server MDS Workflow Integration Service 実行可能ファイルを実行する権限を付与します。 これを行うには、mds_workflow_service ユーザーを追加、**セキュリティ**のタブ、**プロパティ**Microsoft.MasterDataServices.Workflow.exe ので、\<しインストール フォルダー > \Master Data Services\WebApplication\bin と、その mds_workflow_service ユーザー読み取りおよび EXECUTE 権限を付与します。  
  
5.  .NET インストール ユーティリティ (InstallUtil.exe) を使用して、SQL Server MDS Workflow Integration Service をインストールします。 InstallUtil.exe が C:\Windows\Microsoft.NET\Framework\v4.0.30319 など、.NET インストール フォルダーに見つかりません\\です。 SQL Server MDS Workflow Integration Service は、管理者特権のコマンド プロンプトで次のコマンドを入力してインストールします。  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil Microsoft.MasterDataServices.Workflow.exe  
    ```  
  
     インストール中にユーザーの指定を求められたら、mds_workflow_service ユーザーを指定します。  
  
6.  サービス スナップインを使用して、SQL Server MDS Workflow Integration Service を開始します。 これを行うには、サービス スナップインで SQL Server MDS Workflow Integration Service を検索、選択し、をクリックして、**開始**リンクします。  
  
### <a name="create-a-workflow-business-rule"></a>ワークフロー ビジネス ルールの作成  
 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用して、適用時にワークフローを開始するビジネス ルールを作成およびパブリッシュします。 ビジネス ルールには、属性値を変更するアクションを必ず含めて、そのルールが一度適用された後、false と評価されるようにしてください。 たとえば、Price 属性値が 500 より大きく、Approved 属性値が空白の場合に、true と評価されるビジネス ルールがあるとします。 その場合、そのルールに次の 2 つのアクションを含めることができます。1 つは、Approved 属性値を Pending に設定するアクション。もう 1 つは、ワークフローを開始するアクションです。 また、"has changed" 条件を使用するルールを作成し、追跡グループを変更するための属性を追加する方法もあります。 ビジネス ルールの詳細については、次を参照してください。[ビジネス ルール & #40 です。マスター データ サービス &#41;](../../master-data-services/business-rules-master-data-services.md).  
  
 カスタム ワークフローを開始するビジネス ルールを [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] で作成するには、次の手順を実行します。  
  
1.  ビジネス ルール エディターで[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]ドラッグ、ビジネス ルールの条件を指定したら、**ワークフローの開始**からアクション、**外部アクション**の一覧を表示、**し**ペインの**アクション**ラベル。  
  
2.  **アクションの編集** ウィンドウで、**ワークフロー型**ボックスに、ワークフロー ハンドラー アセンブリを識別するタグを入力します。 これは、アセンブリの構成ファイルで指定したタグです (例: TEST)。  
  
3.  必要に応じて、選択、**メンバー データを含める**チェック ボックスをオンします。 これをオンにすると、ワークフロー ハンドラーに渡される XML に、属性の名前と値が含められます。  
  
4.  **ワークフロー サイト**ボックスに、web サイトの名前を入力します。 これは、使用するカスタム ワークフローには該当しない場合がありますが、追加のコンテキスト用に使用できます。  
  
5.  **ワークフロー名**ボックスに、Visual Studio からのワークフローの名前を入力します。 これは、使用するカスタム ワークフローには該当しない場合がありますが、追加のコンテキスト用に使用できます。  
  
6.  ビジネス ルールを作成およびパブリッシュします。  
  
### <a name="apply-business-rules-to-start-a-workflow"></a>ビジネス ルールを適用してワークフローを開始する  
 データにビジネス ルールを適用して、ワークフローを開始します。 これを行うには、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用して、検証するメンバーを含んだエンティティを編集します。 をクリックして**ビジネス ルールを適用**です。 ビジネス ルールへの応答として、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] は、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースの Service Broker キューに値を設定します。 SQL Server MDS Workflow Integration Service は、キューをチェックすると、指定されたワークフロー ハンドラー アセンブリにデータを送信し、キューをクリアします。 ワークフロー ハンドラー アセンブリは、コードに記述された任意のアクションを実行します。  
  
## <a name="troubleshoot-custom-workflows"></a>カスタム ワークフローのトラブルシューティング  
 ワークフロー ハンドラー アセンブリがデータを受け取らなかった場合は、SQL Server MDS Workflow Integration Service をデバッグするか、または Service Broker キューを参照します。  
  
### <a name="debug-sql-server-mds-workflow-integration-service"></a>SQL Server MDS Workflow Integration Service のデバッグ  
 SQL Server Workflow Integration Service をデバッグするには、次の手順に従います。  
  
1.  サービス スナップインを使用して、サービスを停止します。  
  
2.  コマンド プロンプトを開き、サービスの場所に移動した後、コマンド Microsoft.MasterDataServices.Workflow.exe -console を入力してサービスをコンソール モードで実行します。  
  
3.  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] で、メンバーを更新し、ビジネス ルールを再度適用します。 詳細なログがコンソール ウィンドウに表示されます。  
  
### <a name="view-the-service-broker-queue"></a>Service Broker キューの表示  
 ワークフローの一部として渡されるマスター データを含んだ Service Broker キューは、mdm.microsoft/mdm/queue/externalaction です。 キューは含まれて、**オブジェクト エクスプ ローラー** SQL Management Studio のサービス ブローカー ノードの下の[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]データベース。 ただし、サービスがキューを適切にクリアした場合、このキューは空になります。  
  
## <a name="see-also"></a>参照  
 [カスタム ワークフローの例 & #40 です。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)   
 [カスタム ワークフロー XML の説明と #40 です。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md)  
  
  
