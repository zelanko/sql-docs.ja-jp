---
title: 表形式モデル データベースへの接続 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ab3c0ccd3c6c136bfe3e48134c751ca54af832e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="connect-to-a-tabular-model-database"></a>表形式モデル データベースへの接続します。  
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブル モデルを構築し、Analysis Services テーブル モード サーバーに配置したら、クライアント アプリケーションからの使用を可能にするための権限を設定する必要があります。 この記事の説明のアクセス許可をクライアント アプリケーションからデータベースに接続する方法です。  
  
> [!NOTE]  
>  既定では、ファイアウォールを構成するまで、Analysis Services へのリモート接続は利用できません。 クライアント接続の名前付きインスタンスまたは既定のインスタンスを構成する場合は、適切なポートを開いていることを確認する必要があります。 詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご参照ください。  
  
##  <a name="bkmk_userpermissions"></a> データベースに対するユーザー権限  
 テーブル データベースに接続するユーザーには、読み取りアクセスを指定するデータベース ロールのメンバーシップが必要です。  
  
 ロール (および場合によってはロール メンバーシップ) が定義されるのは、モデルが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で作成されるときです。または、配置済みモデルの場合は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]によって使用されるときです。 ロール マネージャーを使用してロールの作成の詳細については[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を参照してください[作成と管理の役割](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)です。 ロール配置済みモデルを作成および管理の詳細については、次を参照してください。[表形式モデル ロール](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)です。  
  
> [!CAUTION]  
>  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のロール マネージャーを使用して定義済みロールを含むテーブル モデル プロジェクトを再配置すると、配置済みテーブル モデルに定義されたロールが上書きされます。  
  
##  <a name="bkmk_admin"></a> サーバーに対する管理権限  
 Excel ブックまたは Reporting Services レポートをホストするために SharePoint を使用している組織では、SharePoint ユーザーがテーブル モデル データを利用できるようにする追加の構成が必要です。 SharePoint を使用していない場合は、このセクションを省略してください。  
  
 テーブル データを含む Excel ブックまたは [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを表示するには、Excel Services または Reporting Services を実行するアカウントに、Analysis Services インスタンスに対する管理権限が必要です。 これらのサービスが Analysis Services インスタンスによって信頼されるようにするには、管理権限が必要です。  
  
#### <a name="grant-administrative-access-on-the-server"></a>サーバーに対する管理アクセス権の付与  
  
1.  サーバーの全体管理で、[サービス アカウントの構成] ページを開きます。  
  
2.  Excel Services によって使用されるサービス アプリケーション プールを選択します。 **[サービス アプリケーション プール - SharePoint Web サービスのシステム]** またはカスタム アプリケーション プールである可能性があります。 Excel Services によって使用される管理アカウントがページに表示されます。  
  
     SharePoint モードの Reporting Services を含む SharePoint ファームでは、Reporting Services サービス アプリケーションのアカウント情報も取得します。  
  
     次の手順では、これらのアカウントを Analysis Services インスタンスのサーバー ロールに追加します。  
  
3.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、サーバー インスタンスを右クリックして **[プロパティ]** を選択します。 オブジェクト エクスプローラーで **[ロール]** を右クリックして、 **[新しいロール]** を選択します。  
  
4.  [Analysis Services のプロパティ] ページで、 **[セキュリティ]** をクリックします。  
  
5.  **[追加]** をクリックし、Excel Services によって使用されるアカウントを入力します。Reporting Services によって使用されるアカウントも続けて入力します。  
  
##  <a name="bkmk_excelconn"></a> Excel または SharePoint からの接続  
 Analysis Services データベースへのアクセスを提供するクライアント ライブラリを使用して、テーブル モード サーバー上で実行される model データベースに接続できます。 ライブラリには、Analysis Services OLE DB プロバイダー、ADOMD.NET、および AMO が含まれています。  
  
 Excel では、OLE DB プロバイダーを使用します。 SQL Server 2008 R2 の MSOLAP.4 (ファイル名 msolap100.dll、バージョン 10.50.1600.1)、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel と共にインストールされる MSOLAP.5 (ファイル名 msolap110.dll) がある場合、テーブル データベースに接続されるバージョンを持っています。  
  
 Excel から model データベースに接続するには、次のいずれかのアプローチを使用します。  
  
-   次のセクションで説明する手順を使用して、Excel 内からデータ接続を作成します。  
  
-   Analysis Services テーブル モード サーバー上で実行されているデータベースへのリダイレクトを提供する BI セマンティック モデル接続 (.bism) ファイルを SharePoint で作成します。 BI セマンティック モデル接続ファイルにより、その接続で指定した model データベースを使用する Excel を起動する右クリック コマンドが提供されます。 Reporting Services がインストールされている場合には、これによって [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] も起動されます。 BI セマンティック モデル接続ファイルの作成および使用の詳細については、「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。  
  
-   データ ソースとしてテーブル データベースを参照する Reporting Services 共有データ ソースを作成します。 SharePoint で共有データ ソースを作成し、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]を起動するために使用できます。  
  
#### <a name="connect-from-excel"></a>Excel からの接続  
  
1.  Excel の **[データ]** タブの **[外部データの取り込み]** で、 **[その他のデータ ソース]** をクリックします。  
  
2.  **[Analysis Services から]** をクリックします。  
  
3.  **[サーバー名]** に、データベースをホストする Analysis Services インスタンスを指定します。 通常、サーバー名は、サーバー ソフトウェアを実行するコンピューターの名前です。 サーバーが名前付きインスタンスとしてインストールされた場合は、この形式で名を指定する必要があります: \<servername >\\< instancename\>です。  
  
     スタンドアロン テーブル配置用にサーバー インスタンスを構成する必要があります。そのサーバー インスタンスには、アクセスを許可する受信の規則が必要です。 詳細については、「 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md) 」および「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を参照してください。  
  
4.  データベースに対する読み取り権限がある場合は、ログオン資格情報について **[Windows 認証を使用する]** を選択します。 それ以外の場合は、 **[以下のユーザー名とパスワードを使用する]** を選択し、データベース権限を持つ Windows アカウントのユーザー名とパスワードを入力します。 **[次へ]** をクリックします。  
  
5.  データベースを選択します。 有効なデータベースを選択すると、データベースの単一の **モデル** キューブが表示されます。 **[次へ]** をクリックし、 **[完了]** をクリックします。  
  
 接続を確立した後は、データを使用して、ピボットテーブルやピボットグラフを作成できます。 詳細については、次を参照してください。 [Excel で分析](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)です。  
  
##  <a name="bkmk_sharepoint"></a> SharePoint からの接続  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を使用している場合は、Analysis Services テーブル モード サーバー上で実行されているデータベースへのリダイレクトを提供する BI セマンティック モデル接続ファイルを SharePoint で作成できます。 BI セマンティック モデル接続により、データベースへの HTTP エンドポイントが提供されます。 また、SharePoint サイト上のドキュメントを定期的に使用するナレッジ ワーカーが簡単にテーブル モデルにアクセスできるようになります。 ナレッジ ワーカーがテーブル モデル データベースにアクセスするために知っておく必要があるのは、BI セマンティック モデル接続ファイルの場所またはその URL だけです。 サーバーの場所やデータベース名に関する詳細は、BI セマンティック モデル接続にカプセル化されます。 BI セマンティック モデル接続ファイルの作成および使用の詳細については、「[Power Pivot BI セマンティック モデル接続 &#40;.bism&#41;](../../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)」および「[テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。  
  
##  <a name="bkmk_Tshoot"></a> 接続の問題のトラブルシューティング  
 このセクションでは、テーブル モデル データベースに接続する際に発生する問題の原因と解決手順について説明します。  
  
 **データ接続ウィザードで、指定したデータ ソースからデータベースのリストを取得できません。**  
  
 データをインポートするときに、リモートの Analysis Services サーバー上の表形式モデル データベースに接続ウィザードを使用しようとして、十分なアクセス許可がないと、この Microsoft Excel エラーが発生します。 このエラーを解決するには、データベースに対するユーザー アクセス権が必要です。 データへのユーザー アクセスの許可については、このトピックの前半で説明している手順を参照してください。  
  
 **外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。次の接続を更新できませんでした:\<モデル名 > サンド ボックス**  
  
 SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。 このエラーは、リモートの Analysis Services サーバーに対する十分な権限がないために発生します。 このエラーを解決するには、データベースに対するユーザー アクセス権が必要です。 データへのユーザー アクセスの許可については、このトピックの前半で説明している手順を参照してください。  
  
 **この操作の実行中にエラーが発生しました。ブックを再読み込みされ、もう一度この操作を実行してください。**  
  
 SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。 このエラーは、Excel Services が、モデル データが配置されている Analysis Services インスタンスによって信頼されていないために発生します。 このエラーを解決するには、Analysis Services インスタンスに対する Excel Services の管理権限を付与します。 管理権限の付与については、このトピックの前半で説明している手順を参照してください。 エラーが引き続き発生する場合は、Excel Services アプリケーション プールを再利用します。  
  
 **ブックで使用されている外部データ ソースへの接続を確立しようとするとエラーが発生しました。**  
  
 SharePoint では、モデル データを使用するピボットテーブルでデータのフィルター処理などのデータ操作を実行しようとすると、この Microsoft Excel エラーが発生します。 このエラーは、ユーザーがブックに対する十分な SharePoint 権限を持っていないために発生します。 ユーザーには、 **読み取り** 権限以上の権限が必要です。 データにアクセスするには、**表示のみ** 権限では不十分です。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル ソリューションの配置](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
