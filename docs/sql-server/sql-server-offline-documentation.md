---
title: 以前のバージョンの SQL Server ドキュメントをオフラインでインストールする
description: SQL Server 2019、2017、2016、2014、および 2012 のオフライン ドキュメントをインストールする方法について説明します。 オフライン コンテンツを表示するには、SQL Server Management Studio (SSMS) を使用します。
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.date: 04/20/2020
ms.openlocfilehash: 1420e18fbf335e22d44bf78d526ab35c8b1434e5
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087872"
---
# <a name="install-previous-versions-of-sql-server-documentation-to-view-offline-in-ssms"></a>SSMS で以前のバージョンの SQL Server ドキュメントをインストールしてオフラインで表示する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、[SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) で SQL Server のオフライン コンテンツをダウンロードして表示する方法について説明します。 オフライン コンテンツを使用すると、インターネットに接続しなくてもドキュメントにアクセスできます (ただし、ダウンロードするにはインターネット接続が必要です)。

オフライン ドキュメントは、以前のバージョンの SQL Server の一部について入手できます。 [以前のバージョンのコンテンツをオンラインで表示](https://docs.microsoft.com/previous-versions/sql/)することもできますが、オフライン オプションを使用すると、以前のコンテンツに簡単にアクセスできます。

## <a name="how-to-download-and-configure-offline-content"></a>オフライン コンテンツをダウンロードして構成する方法

オンライン ソースまたはローカル ディスクから SQL Server ヘルプ パッケージをダウンロードしてインストールできます。 以下のセクションでは、SQL Server のさまざまなバージョンのオフライン コンテンツを読み込む方法について説明しています。

- [SQL Server 2019](#sql2019)
- [SQL Server 2017](#sql2017)
- [SQL Server 2016](#sql2016)
- [SQL Server 2014](#sql2014)
- [SQL Server 2012](#sql2012)

## <a name="sql-server-2019"></a><a id="sql2019"></a> SQL Server 2019

SQL Server 2019 のオフライン ドキュメントを読み込むには、次の手順を実行します。

1. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

2. SQL Server 2019 の最新のヘルプ コンテンツを見つけるには、 **[コンテンツの管理]** タブの [インストール元] で **[オンライン]** を選択し、検索バーに「*sql server 2019*」と入力します。

   ![ヘルプ ビューアーの SQL Server 2019 のドキュメント検索](../sql-server/media/sql-server-help-installation/sql-2019-search.png)

   > [!Note]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツのインストール先が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。 ローカル ストア パスの変更後にヘルプのインストールに失敗した場合は、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

3. SQL Server 2019 の最新のヘルプ コンテンツをインストールするには、インストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、右下の **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2019 ブックの追加と更新](../sql-server/media/sql-server-help-installation/sql-2019-add-update.png)

   > [!NOTE]
   > コンテンツの追加中にヘルプ ビューアーがフリーズ (ハング) した場合は、%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings ファイル内の Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

4. SQL Server 2019 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2019*」を検索します。

   ![自動的に更新された SQL Server 2019 ブック](../sql-server/media/sql-server-help-installation/sql-2019-content.png)

## <a name="sql-server-2017"></a><a id="sql2017"></a> SQL Server 2017

SQL Server 2017 のオフライン ドキュメントを読み込むには、次の手順を実行します。

1. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

2. SQL Server 2017 の最新のヘルプ コンテンツを見つけるには、 **[コンテンツの管理]** タブの [インストール元] で **[オンライン]** を選択し、検索バーに「*sql server 2017*」と入力します。

   ![ヘルプ ビューアーでの SQL Server 2017 ブックの検索](../sql-server/media/sql-server-help-installation/sql-2017-search.png)

   > [!Note]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツのインストール先が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。 ローカル ストア パスの変更後にヘルプのインストールに失敗した場合は、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

3. SQL Server 2017 の最新のヘルプ コンテンツをインストールするには、インストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、右下の **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2017 ブックの追加と更新](../sql-server/media/sql-server-help-installation/sql-2017-add-update.png)

   > [!NOTE]
   > コンテンツの追加中にヘルプ ビューアーがフリーズ (ハング) した場合は、%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings ファイル内の Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

4. SQL Server 2017 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2017*」を検索します。

   ![自動的に更新された SQL Server 2017 ブック](../sql-server/media/sql-server-help-installation/sql-2017-content.png)

## <a name="sql-server-2016"></a><a id="sql2016"></a> SQL Server 2016

SQL Server 2016 のオフライン ドキュメントを読み込むには、次の手順を実行します。

1. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

2. SQL Server 2016 の最新のヘルプ コンテンツを見つけるには、 **[コンテンツの管理]** タブの [インストール元] で **[オンライン]** を選択し、検索バーに「*sql server 2016*」と入力します。

   ![ヘルプ ビューアーでの SQL Server 2016 ブックの検索](../sql-server/media/sql-server-help-installation/sql-2016-search.png)

   > [!Note]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツのインストール先が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。 ローカル ストア パスの変更後にヘルプのインストールに失敗した場合は、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

3. SQL Server 2016 の最新のヘルプ コンテンツをインストールするには、インストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、右下の **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2016 ブックの追加と更新](../sql-server/media/sql-server-help-installation/sql-2016-add-update.png)

   > [!NOTE]
   > コンテンツの追加中にヘルプ ビューアーがフリーズ (ハング) した場合は、%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings ファイル内の Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

4. SQL Server 2016 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2016*」を検索します。

   ![自動的に更新された SQL Server 2016 ブック](../sql-server/media/sql-server-help-installation/sql-2016-content.png)

## <a name="sql-server-2014"></a><a id="sql2014"></a> SQL Server 2014

SQL Server 2014 のオフライン ドキュメントを読み込むには、次の手順を実行します。

1. 「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2014 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=42557)」をダウンロード センターからダウンロードし、フォルダーに保存します。

2. ファイルを解凍して .msha ファイルを表示します。

   ![SQL Server 2014 ヘルプ ドキュメントのセットアップ ファイル](../sql-server/media/sql-server-help-installation/sql-2014-help-content-setup-msha.png)

3. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

4. 最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。
   ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

5. コンテンツを解凍したフォルダーを見つけます。 フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。

   ![SQL Server 2014 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-help-installation/sql-2014-open-msha.png)

6. 検索バーに「*sql server 2014*」と入力します。 入手できる 2014 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの検索](../sql-server/media/sql-server-help-installation/sql-2014-search.png)

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの追加と更新](../sql-server/media/sql-server-help-installation/sql-2014-add-update.png)

    > [!NOTE]
    > コンテンツの追加中にヘルプ ビューアーがフリーズ (ハング) した場合は、%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings ファイル内の Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

7. SQL Server 2014 のコンテンツがインストールされたことを確認するには、左側のコンテンツ ペインで「*sql server 2014*」を検索します。

   ![自動的に更新された SQL Server 2014 ブック](../sql-server/media/sql-server-help-installation/sql-2014-content.png)

## <a name="sql-server-2012"></a><a id="sql2012"></a> SQL Server 2012

SQL Server 2012 のオフライン ドキュメントを読み込むには、次の手順を実行します。

1. 「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2012 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=35750)」をダウンロード センターからダウンロードし、フォルダーに保存します。

2. ファイルを解凍して .msha ファイルを表示します。

   ![SQL Server 2012 のヘルプ コンテンツ セットアップ ファイル](../sql-server/media/sql-server-help-installation/sql-2012-help-content-setup-msha.png)

3. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

4. 最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。
   ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

5. コンテンツを解凍したフォルダーを見つけます。 フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。

   ![SQL Server 2012 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-help-installation/sql-2012-open-msha.png)

6. 検索バーに「*sql server 2012*」と入力します。 入手できる 2012 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの検索](../sql-server/media/sql-server-help-installation/sql-2012-search.png)

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの追加と更新](../sql-server/media/sql-server-help-installation/sql-2012-add-update.png)

    > [!NOTE]
    > コンテンツの追加中にヘルプ ビューアーがフリーズ (ハング) した場合は、%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings ファイル内の Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

7. SQL Server 2012 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2012*」を検索します。

   ![自動的に更新された SQL Server 2012 ドキュメント](../sql-server/media/sql-server-help-installation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>オフライン ドキュメントを表示する

SQL Server のヘルプ コンテンツは、最新バージョンの [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) の **[ヘルプ]** メニューを使用して表示できます。

### <a name="view-offline-help-content-in-ssms"></a>SSMS でオフライン ヘルプ コンテンツを表示する

インストールされているヘルプを SSMS で表示するには、[ヘルプ] メニューから **[ヘルプ ビューアーで起動]** を選択してヘルプ ビューアーを起動します。

   ![ヘルプ ビューアーで起動](../sql-server/media/sql-server-help-installation/helpviewer-view-offline.png)  

ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。このタブの左側のペインにインストールされたヘルプの目次が表示されます。 目次内の記事を選択すると、右側のペインに該当するトピックが表示されます。

> [!TIP]
> コンテンツ ペインが表示されない場合は、左余白の [コンテンツ] を選択します。 プッシュピン アイコンを選択すると、コンテンツ ペインは開いたままになります。  

   ![コンテンツが表示されたヘルプ ビューアー](../sql-server/media/sql-server-help-installation/view-offline-all.png)

## <a name="life-cycle-policy"></a>ライフサイクル ポリシー

特定の製品、サービス、またはテクノロジがどのようにサポートされているかについては、Microsoft 製品のライフサイクルを参照してください。

- [Microsoft ライフサイクル ポリシー](https://support.microsoft.com/lifecycle/selectindex)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>次のステップ

アーカイブされたコンテンツとヘルプ ビューアーの詳細については、以下のリンクを参照してください。

- [以前のバージョンの SQL Server ドキュメントへの直接リンク](https://docs.microsoft.com/previous-versions/sql/)
- [Microsoft ヘルプ ビューアー - Visual Studio](https://docs.microsoft.com/visualstudio/help-viewer/overview)
- [SQL Server ドキュメント、スタート](../sql-server/index.yml?view=sql-server-2016)
- [SQL ドキュメントのバージョン管理システム](../sql-server/versioning-system-monikers-ui-sql-server.md?view=sql-server-2016)