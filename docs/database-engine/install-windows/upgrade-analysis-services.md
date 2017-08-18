---
title: "Analysis Services のアップグレード | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
caps.latest.revision: 79
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3b3ad4ecf62f3a30882720140f2f362007f8428b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="upgrade-analysis-services"></a>Analysis Services のアップグレード
  Analysis Services インスタンスを同じサーバー モードの SQL Server バージョンにアップグレードすると、「[Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)」で説明する、最新リリースで導入された機能を利用できます。  
  
 同じハードウェアで実行されている他のインスタンスとは独立して、各インスタンスをインプレース アップグレードできます。 ほとんどの管理者は、実稼働ワークロードを新しいサーバーに転送する前にアプリケーションをテストするために、新しいバージョンの新しいインスタンスをインストールしますが、 開発サーバーやテスト サーバーでは、インプレース アップグレードの方が便利な場合があります。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にアップグレードする前に、次のトピックを確認してください。  

- 「[SQL Server 2017 リリース ノート](../../sql-server/sql-server-2017-release-notes.md)」には、既知の問題と回避策が記載されています。  
- 「[SQL Server 2016 リリース ノート](../../sql-server/sql-server-2016-release-notes.md)」には、既知の問題と回避策が記載されています。  
- 提供中止、非推奨、または変更になった Analysis Services の機能については、「[Analysis Services の旧バージョンとの互換性](../../analysis-services/analysis-services-backward-compatibility.md) 」を参照してください。 これらの一覧を定期的に確認して、モデル、スクリプト、またはカスタム コードへの製品の変更の影響を評価する必要があります。 通常、機能の移行は次期メジャー リリースのプレリリース中に発表されます。  
  
## <a name="server-upgrade"></a>サーバーのアップグレード  
 サーバーとデータベースをアップグレードする場合、次の 2 つの基本的な方法があります。  
  
-   **インプレース アップグレード** では、既存のプログラム ファイルが [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のプログラム ファイルに置き換えられます。 データベースは、同じ場所に残ります。 プログラム フォルダーは、新しい名前を反映して更新されます。  
  
-   **サイド バイ サイド アップグレード** では、同時にハードウェアをアップグレードする場合を除き、通常は同じコンピューター上に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新しいインストールが作成されます。 この方法では、データベースを新しいインスタンスに移動し、必要に応じて前のバージョンをアンインストールしてディスク領域を解放する必要があります。  
  
 特定のサーバーに接続されているデータベースの互換性レベルは、手動で変更しない限り、同じレベルのままになります。  
  
### <a name="in-place-upgrade"></a>インプレース アップグレード  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既存のインスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, auの既存のインスタンスをmatically migrate existing databases from the old instance の既存のインスタンスを the new instance. メタデータおよびバイナリ データは 2 つのバージョン間で互換性があるため、アップグレード後もそのまま使用できます。手動でデータを移行する必要はありません。  
  
 既存のインスタンスをアップグレードするには、セットアップを実行し、新しいインスタンスの名前として既存のインスタンス名を指定します。  
  
### <a name="side-by-side-upgrade"></a>サイド バイ サイド アップグレード  
  
-   すべてのデータベースをバックアップし、それぞれ復元できることを確認します。 詳細については、「 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。  
  
-   アップグレード後のサーバーの動作を確認するための基礎として後で使用する、レポート、スプレッドシート、またはダッシュ ボード スナップショットのサブセットを特定します。 可能であれば、アップグレードしたサーバーで同じワークロードを比較できるように、パフォーマンス測定値を収集します。  
  
-   置き換えるサーバーと同じサーバー モード (表形式または多次元) を選択して、Analysis Services の新しいインスタンスをインストールします。 詳細については、｢ [Analysis Services のインストール](../../analysis-services/instances/install-windows/install-analysis-services.md)」を参照してください。  
  
     インストール後のタスクに従って、ポートを構成し、サーバー管理者を追加します。 詳細については、「[インストール後の構成 &#40;Analysis Services&#41;](../../analysis-services/instances/post-install-configuration-analysis-services.md)」を参照してください。  
  
-   各データベースを接続または復元します。  
  
-   DBCC を実行して、データベースの整合性をチェックします。 表形式モデルでは、モデル階層全体にわたって孤立したオブジェクトがないかどうかをテストして、徹底したチェックが行われます。 多次元モデルでは、パーティション インデックスだけがチェックされます。 詳細については、「[Analysis Services の表形式および多次元データベース用 Database Consistency Checker &#40;DBCC&#41;](../../analysis-services/instances/database-consistency-checker-dbcc-for-analysis-services.md)」を参照してください。  
  
-   レポート、スプレッドシート、ダッシュボードをテストして、動作や計算に問題となるような変化がないことを確認します。 多次元と表形式のどちらのワークロードでも、パフォーマンスが向上していることを確認する必要があります。  
  
-   ログインやアクセス許可の問題を解決して、処理動作をテストします。 接続に既定のサービス アカウントを使用している場合、新しいサービスは別のアカウントで実行されます。 Analysis Services 開始アカウントの詳細については、「[サービス アカウントの構成 &#40;Analysis Services&#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md)」を参照してください。   
  
-   新しいサーバー名を使用するようにスクリプトを調整して、アップグレードされたサーバーでバックアップおよび復元操作をテストします。  
  
## <a name="database-upgrade"></a>データベースのアップグレード  
 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースは、アップグレード後のサーバー上で、古いデータベース互換性レベル設定で実行されます。 一般に、新機能にアクセスできるようにするために、データベースまたはモデルをアップグレードして、より高い互換性レベルで運用できますが、これを行うと、サーバーの特定のバージョンにバインドされることに注意してください。  
  
 データベースをアップグレードするには、通常、SQL Server Data Tools (SSDT) でモデルをアップグレードし、アップグレードされたサーバー インスタンスにソリューションを展開します。 最新バージョンを入手する場合は、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx) 」をご覧ください。  
  
 表形式データベースと多次元データベースは、異なるバージョン パスに従います。 多次元モデルと表形式モデルの互換性レベルがどちらも 1100 であるのは偶然です。  機能の変更がどちらか一方にのみ影響する場合、モードは異なる速度で進歩することになります。  
  
 基礎知識を得るために、次の表には互換性レベルがまとめられていますが、詳細トピックを確認して、各レベルが提供する機能を把握する必要があります。  
  
||||  
|-|-|-|  
|テーブル|1200|SQL Server 2016|  
|テーブル|1103|SQL Server 2014|  
|テーブル|1100|SQL Server 2012|  
|多次元|1100|SQL Server 2012 以降|  
|多次元|1050|SQL Server 2005、2008、2008 R2|  
  
 詳細については、「[多次元データベースの互換性レベル &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)」および「[Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。  
  
## <a name="tabular-model-upgrade-to-1200-compatibility-level"></a>互換性レベル 1200 への表形式モデルのアップグレード  
 表形式モデルと表形式データベースは、SQL Server 2016 から最大のメリットが得られます。 このリリースでは、互換性レベル 1200 の表形式モデルの DirectQuery モードの変更、ハイブリッド モデルの削除による簡素化、設計時にデータのサブセットを取得するためのクエリ ステートメントの追加が行われており、バックエンド データベースの行のアクセス許可ではなく、DAX による行レベルのセキュリティが提供されます。  
  
 アップグレードするもう 1 つの理由は、モデル内の新しい表形式のメタデータ構造です。 新しい互換性レベル 1200 の表形式モデルでは、モデルがこのレベルで作成されたのか、このレベルにアップグレードされたのかに関係なく、オブジェクトの定義にネイティブの用語 (モデル、テーブル、リレーションシップ、列など) を使用して主要要素を記述します。  
  
 表形式モデルをアップグレードするには、このリリース用に構築されたバージョンの [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx) を使用して、 **互換性レベル** プロパティを **SQL Server 2016 RTM (1200)**に変更します。  
  
 SSMS、コード、またはスクリプトを使用して **CompatibilityLevel**を変更しないでください。 単独ではプロパティを変更しても何も実行されません。 プロパティの更新に対応して SSDT でメタデータの変換が実行された後、プロジェクトを再度開きます。  
  
 いつものように、アップグレード前のバージョンに戻す必要がある場合に備えて、アップグレードする前にモデルのバックアップを必ず保存しておいてください。  
  
1.  [SSDT] > [ソリューション エクスプローラー] で、**[model.bim]** を右クリックし、**[コードの表示]** を選択して、モデルが閉じられ、新しいウィンドウ (コード ウィンドウ) で再度開かれることを確認します。  
  
2.  モデルは XMLA ドキュメントとして開きます。 変換後の比較のために、内容を別のファイルにコピーします (SSDT で新しい XML ファイルを開くことができます)。  
  
3.  **[model.bim]** を右クリックし、 **[デザイナーの表示]**に変更します。  
  
4.  **CompatibilityLevel** を  **SQL Server 2016 RTM (1200)**に設定します。  
  
5.  この手順は元に戻すことができないため、操作の確認を求められます。 **[はい]** をクリックして続行します。 プロジェクトが更新されます。  
  
6.  **[model.bim]** を右クリックし、 **[コードの表示]**に変更します。  
  
     表形式のメタデータを使用して、モデル定義が JSON で表示されます。  
  
 **メタデータの変換**  
  
 変換後と変換前のメタデータを比較すると、メタデータが JSON に変換され、冗長な定義が削除されていることがわかります。  
  
 モデルにはすべての機能が保持されます。データ バインド、パーティション スライス、式、オブジェクト識別子、オブジェクト名、説明、キャプション、翻訳、注釈がそのまま保持されます。 ただし、コードやスクリプトで特定のオブジェクトを参照している場合は、コードの書き換えの一環として、存在しなくなったオブジェクトへの参照を削除します。 たとえば、1050 または 1103 モデルには、キューブの外部にあるディメンションのセクションがあるのに対し、1200 モデルでは 1 つのオブジェクトとしてテーブルを定義します。  
  
> [!NOTE]  
>  表形式の古い互換性レベルの 1050 と 1103 はサポートされてはいますが、使用されなくなりました。 SQL Server の将来のリリースでは、多次元オブジェクトとしてキャストされた表形式モデルはサポートされなくなります。 詳細については、「 [SQL Server 2016 に含まれている非推奨の Analysis Services 機能](../../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md) 」を参照してください。  
  
## <a name="post-upgrade-for-tabular-models-at-1200-compatibilitylevel"></a>互換性レベル 1200 の表形式モデルのアップグレード後  
 モデルが変換されたら、XMLA ではなく、[表形式モデル スクリプト言語 &#40;TMSL&#41; リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) を使用してデータベース操作のスクリプトを作成します。 TMSL は、モデルが 1200 の場合に SSMS で自動的に生成されます。 1200 の表形式データベースを対象とするカスタム コードでは、Microsoft.AnalysisServces.Tabular 名前空間で定義された API を使用する必要があります。 スクリプトとコードは一から作成する必要があります。組み込みの変換のメカニズムはありません。 概要情報については、「 [開発者ガイド (Analysis Services)](../../analysis-services/analysis-services-developer-documentation.md) 」をご覧ください。  
  
 互換性レベル 1200 でのみサポートされる次の機能を表形式モデルに追加することもできます。  
  
-   モデルでの DAX による行レベルのセキュリティ、より多くのデータ ソース、モデリング用のデータ サブセット、および簡素化された構成をサポートする DirectQuery 実装  
  
-   計算列  
  
-   表示フォルダー  
  
## <a name="upgrade-tabular-models-in-directquery-mode"></a>DirectQuery モードの表形式モデルのアップグレード  
 DirectQuery 用に構成された古い表形式モデルのインプレース アップグレードは実行できません。 DirectQuery の新しい実装では、構成のフットプリントが小さくなっているので、すべての設定を移植できるわけではありません。  
  
1.  SSDT で **DirectQuery** モードをオフにし、モデルでインメモリ ストレージが使用されるようにします。 手順については、「 [SSDT での DirectQuery デザイン モードの有効化](https://msdn.microsoft.com/library/hh270245.aspx) 」を参照してください。  
  
2.  **CompatibilityLevel** を SQL Server 2016 (RTM) 1200 に設定します。  
  
3.  モデルを保存し、リビルドまたは展開します。  
  
4.  **DirectQuery** を有効にします。 詳細については、「 [DirectQuery for Tabular 1200 models](http://msdn.microsoft.com/library/4227977e-7368-4d45-b78f-24076882e7a8) 」(表形式 1200 モデル用 DirectQuery) を参照してください。  
  
## <a name="see-also"></a>参照  
 [DirectQuery モード &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Power Pivot for SharePoint のアップグレード](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [多次元モードおよびデータ マイニング モードでの Analysis Services のインストール](http://msdn.microsoft.com/library/8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60)   
 [インストール ウィザードを使用した SQL Server 2016 へのアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  

