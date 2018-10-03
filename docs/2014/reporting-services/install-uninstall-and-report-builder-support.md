---
title: インストール、アンインストール、およびレポート ビルダーのサポート |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- administering Report Builder
ms.assetid: 2c9a5814-17bf-4947-8fb3-6269e7caa416
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 284a99d74e8b0aa2e3c3b47cc1f277df537b7e9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168782"
---
# <a name="install-uninstall-and-report-builder-support"></a>レポート ビルダーのインストール、アンインストール、およびサポート
  レポート ビルダーは、レポート、レポート パーツ、および共有データセットの作成、更新、および共有に使用できるレポート作成ツールです。 レポート ビルダーは 2 つのバージョンで使用できます: スタンドアロンと[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]します。 スタンドアロン バージョンは、ユーザーまたは管理者によってコンピューターにインストールされます。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]でバージョンが自動的にインストールされている[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]レポート マネージャーまたは統合された SharePoint サイトからコンピューターにダウンロードおよび[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
 レポート ビルダーのスタンドアロン バージョンがインストールされていない[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。 [Microsoft® SQL Server® 2012 レポート ビルダー](http://go.microsoft.com/fwlink/?LinkId=401502)から個別にダウンロードしてインストールする必要があります。  
  
> [!NOTE]  
>  レポート ビルダーは、Itanium ベースのコンピューターにはインストールできません。 これに適用されます、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]およびレポート ビルダーのスタンドアロン バージョンです。  
  
 管理者は、通常、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のインストールと構成、レポート ビルダーの [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] バージョンを使用するための権限の許可、フォルダーの管理とレポート サーバーに保存されたレポート、レポート パーツ、および共有データセットに対する権限の管理を行います。 詳細については[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]管理を参照してください[Reporting Services レポート サーバー&#40;ネイティブ モード&#41;](report-server/reporting-services-report-server-native-mode.md)で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][オンライン ブックの「](http://go.microsoft.com/fwlink/?LinkId=154888) msdn.microsoft.com します。  
  
##  <a name="Installing"></a> レポート ビルダーのインストール  
 レポート ビルダーは、スタンドアロンと[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]バージョン。 スタンドアロン バージョンをコンピューターにインストールされ、管理者、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]でバージョンがインストールされている[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]します。 レポート ビルダーは、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=186083)からダウンロードできます。  
  
> [!NOTE]  
>  レポート ビルダーは、Itanium 64 ベースのコンピューターにはインストールできません。 これに適用されます、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]およびレポート ビルダーのスタンドアロン バージョンです。  
  
 レポート ビルダーのいずれかのバージョンをインストールする場合は、事前にシステム要件を確認し、必須コンポーネントをすべてインストールしてください。  
  
### <a name="system-requirements"></a>システム要件  
 レポート ビルダーである必要があります、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]バージョン 3.5 がローカル コンピューターにインストールされています。 場合、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]がインストールされていないローカル コンピューターにインストールするときにレポート ビルダーで求められます続行してインストールを完了する前にインストールします。  
  
 .NET Framework 3.5 は無償です。 .NET Framework 3.5 は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=110520)からダウンロードできます。  
  
 レポート ビルダーをインストールするにはいずれかで[!INCLUDE[msCoName](../includes/msconame-md.md)]をサポートする Windows オペレーティング システム、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5。 たとえば、Windows Vista または Windows 7 にレポート ビルダーをインストールできます。  
  
 レポート ビルダーを実行するコンピューターには 512 MB の RAM があることが推奨されます。 ただし、実行するレポートの複雑さによっては、必要な RAM が増減することがあります。  
  
### <a name="installing-the-stand-alone-version-of-report-builder-directly-on-your-computer"></a>コンピューターへのスタンドアロン バージョンのレポート ビルダーの直接インストール  
 レポート ビルダーは、ダウンロード サイトの [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=186083)からインストールします。または、ユーザーがインストール元として使用できる共有ドライブ上に、レポート ビルダーの Windows インストーラー パッケージである ReportBuilder3.msi ファイルを管理者が配置します。  
  
 また、コマンド ラインからインストールを実行して、サイレント インストールの実行、インストールのログ ファイルの書き込みなどのオプションを含めることもできます。 使用可能なオプションについては、.msi ファイルを実行する Windows インストーラーのマニュアルを参照してください。  
  
 詳細については、次を参照してください。[レポート ビルダーのスタンドアロン バージョンをインストール&#40;レポート ビルダー&#41;](install-windows/install-report-builder.md)します。  
  
 管理者は、Microsoft Systems Management Server (SMS) などのソフトウェアを使用してユーザーのコンピューターにプログラムをプッシュすることもできます。 特定のソフトウェアを使用してレポート ビルダーをインストールする方法については、そのソフトウェアのマニュアルを参照してください。   
  
### <a name="installing-the-clickonce-version-of-report-builder-on-your-computer"></a>コンピューターへの ClickOnce バージョンのレポート ビルダーのインストール  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]でレポート ビルダーのバージョンがインストールされている[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]します。 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] のネイティブでのインストールと SharePoint 統合でのインストールの両方でインストールされます。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] は、Windows アプリケーションを配置するための Microsoft テクノロジです。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] では、Web ページ上でリンクをクリックすることによって、レポート ビルダーのような Windows アプリケーションをインストールおよび実行することができます。 展開の詳細については[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]を適用するアプリケーション[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションのセキュリティ、または実行中の[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]インターネット ゾーン内のアプリケーションは、「ClickOnce 展開 Windows フォーム アプリケーションの」、"セキュリティを参照してください。Windows Forms Overview"または「Trusted Application Deployment Overview」の記事で、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Developer Network Web サイトで[www.microsoft.com/msdn](http://www.microsoft.com/msdn)します。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]バージョンのレポート ビルダーは、レポート サーバー上にありをクリックすると、コンピューターにインストール、**レポート ビルダー**レポート マネージャーでのボタンまたはをクリックして、**レポート ビルダー レポート**オプションを**新しいドキュメント**SharePoint ライブラリ内のメニュー。  
  
> [!NOTE]  
>  **[新しいドキュメント]** メニューに **[レポート ビルダー レポート]** オプション、 **[レポート ビルダーのモデル]** オプション、および **[レポート データ ソース]** オプションが表示されない場合、それらのコンテンツの種類を SharePoint ライブラリに追加する必要があります。   
  
 レポート ビルダーは、レポート マネージャーまたは SharePoint ライブラリから開くことができます。 レポート ビルダーを開く方法の詳細については、次を参照してください。[レポート ビルダーの起動&#40;レポート ビルダー&#41;](report-builder/start-report-builder.md)します。  
  
### <a name="report-builder-languages"></a>レポート ビルダーの言語  
 レポート ビルダーは、英語に加えて 21 か国語で使用できます。 レポート ビルダーのスタンドアロン バージョンをダウンロードする場合は、インストールする言語バージョンを選択します。 使用する言語バージョンごとにダウンロードを繰り返す必要があります。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] バージョンの場合は、[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] のインストール時に、すべての言語バージョンがレポート サーバーにインストールされます。 ユーザーのコンピューターのカルチャに応じて、コンピューターにインストールする言語バージョンが判断されます。 カルチャと利用可能なレポート ビルダーの言語が一致しない場合は、英語バージョンがインストールされます。  
  
 次の表に、使用可能な言語バージョンに関する情報を示します。  
  
|LCID (LCID)|[言語]|カルチャ|  
|----------|--------------|-------------|  
|1028|中国語 (繁体字)|zh-TW|  
|1029|チェコ語|cs-CZ|  
|1030|デンマーク語|da-DK|  
|1031|ドイツ語|de-DE|  
|1032|ギリシャ語|el-GR|  
|1033|英語|ja-JP|  
|1035|フィンランド語|fi-FI|  
|1036|フランス語|fr-FR|  
|1038|ハンガリー語|hu-HU|  
|1040|イタリア語|it-IT|  
|1041|日本語|ja-JP|  
|1042|韓国語|ko-KR|  
|1043|オランダ語|nl-NL|  
|1044|ノルウェー語 (ブークモール)|nb-NO|  
|1045|ポーランド語|pl-PL|  
|1046|ポルトガル語 (ブラジル)|pt-BR|  
|1049|ロシア語|ru-RU|  
|1053|スウェーデン語|sv-SE|  
|1055|トルコ語|tr-TR|  
|2052|中国語 (簡体字)|zh-CN|  
|2070|ポルトガル語 (ポルトガル)|pt-PT|  
|3082|スペイン語 (スペイン)|es-ES|  
  
  
##  <a name="Uninstalling"></a> レポート ビルダーをアンインストールします。  
 スタンドアロン バージョンのレポート ビルダーは、コントロール パネルまたはコマンド ラインからアンインストールできます。 これは、スタンドアロン バージョンのレポート ビルダーのみです。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]レポート ビルダーのアンインストールできないとは別にします。 これがインストールおよびアンインストールを常に[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
 詳細については、次を参照してください。[レポート ビルダーのスタンドアロン バージョンをアンインストール&#40;レポート ビルダー&#41;](install-windows/uninstall-report-builder.md)します。  
  
  
##  <a name="Supporting"></a> レポート ビルダーのサポート  
 レポート作成者を支援するために、管理者は、レポート サーバー上のフォルダー、レポート、およびレポート関連アイテムを管理する必要があります。また、レポート サーバー上のリソースに対する権限を許可し、レポート サーバーにアクセスできるように構成する必要があります。  
  
### <a name="folders-reports-and-report-related-items"></a>フォルダー、レポート、およびレポート関連アイテム  
 次のフォルダー、レポート、およびレポート関連アイテムをレポート サーバー上で管理します。  
  
-   レポート、共有データ ソース、モデルなどを保存するフォルダー。  
  
-   個人用レポート。レポートとレポート関連アイテムを保存するプライベート フォルダーです。  
  
-   共有データ ソース。これにより、レポート作成者はレポートの外部に保存されているデータ ソースを使用できます。  
  
-   共有データセット。複数のユーザーが複数のレポートでそのまま使用できるクエリされたデータを提供できます。  
  
-   テーブルやグラフなどのレポート パーツ。これにより、ユーザーはコラボレーション環境で他のユーザーによって作成されたレポートのパーツを拡張したり再利用したりできます。  
  
-   レポート モデル。複雑なデータ ソースからレポート用のデータを簡単に取得できるようになります。  
  
-   背景画像やロゴなどの画像。複数のレポートで使用でき、簡単に管理できるようにレポートの外部に保存されます。  
  
 詳細については、次を参照してください。[レポート サーバー コンテンツの管理&#40;SSRS ネイティブ モード&#41;](report-server/report-server-content-management-ssrs-native-mode.md)で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][オンライン ブックの「](http://go.microsoft.com/fwlink/?LinkId=154888) msdn.microsoft.com します。  
  
### <a name="permissions"></a>アクセス許可  
 レポート サーバーに対する権限は管理者が付与します。 レポート ビルダーのユーザーがレポート サーバーのコンテンツや機能にアクセスするには、レポート サーバーに対する権限が必要です。 たとえば、レポート サーバーに保存されているレポート パーツの使用、レポートの更新と更新したレポートのレポート サーバーへの再保存、レポート マネージャーでのレポートの実行などが必要になる場合があります。 ニーズや実行するタスクに応じて、低い権限または高い権限を許可します。 たとえば、共有レポートを開くことだけが必要なユーザーには、共有レポートを変更する必要があるユーザーに比べて低い特権が設定された権限を許可します。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] がネイティブ モードでインストールされている場合、管理者は次のタスクを実行できます。  
  
-   個人用レポート機能を有効にして、独自のレポートを作成して保存するためのプライベート フォルダーをユーザーに提供します。  
  
-   パブリック フォルダーでレポート ビルダー ロールを使用して、ユーザーが共有レポートのコピーを開き、変更したバージョンをプライベート フォルダーに保存できるようにします。  
  
-   パブリッシャー ロールを使用して、ユーザーがパブリック フォルダー内のレポートおよび共有データ ソースを管理できるようにします。 このロールは、経験豊富なユーザーに割り当てます。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] が SharePoint 統合モードでインストールされている場合、管理者は次のタスクを実行できます。  
  
-   既定で閲覧者グループに許可されている読み取り権限レベルを使用して、ユーザーがパブリック フォルダー内のレポートのコピーを開き、変更したレポートをプライベート フォルダーまたは自分のコンピューターに保存できるようにします。  
  
-   既定でメンバー グループに許可されている投稿権限レベルを使用して、ユーザーがパブリック フォルダー内のレポートおよび共有データ ソースを管理できるようにします。 このレベルの権限は、経験豊富なユーザーに許可します。  
  
 アクセス許可の作成とロールの使用に関する概要については、次を参照してください。、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]ドキュメント[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][オンライン ブックの「](http://go.microsoft.com/fwlink/?LinkId=154888) msdn.microsoft.com します。  
  
### <a name="configuration-of-report-server"></a>レポート サーバーの構成  
 レポート ビルダーでレポートを作成し、Windows Vista、Windows Server 2008、または Windows 7 にインストールされている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続する場合、レポートを開くか保存するためにレポート サーバーにアクセスしようとすると、アクセス拒否エラーが発生する可能性があります。 これは、Windows Vista、Windows Server 2008、および Windows 7 のユーザー アカウント制御 (UAC) というセキュリティ機能が原因です。この機能では、高度な権限の乱用を防ぐために、アプリケーションにアクセスする際に管理者権限が削除されます。  
  
 ただし、追加の構成を行うことによって、レポート ビルダーのユーザーはレポート サーバーを使用できるようになります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の URL を信頼済みサイトに追加できます。 既定では、Windows Vista、Windows Server 2008、および Windows 7 の Internet Explorer 7.0 以降は保護モードで実行されます。 保護モードとは、同じコンピューターで実行されている高レベルのプロセスにブラウザーの要求が到達するのを防ぐ機能です。 レポート サーバー アプリケーションを信頼済みサイトに追加することで、それらのアプリケーションに対して保護モードを無効にすることができます。 この変更を行うには、管理者権限が必要です。  
  
 構成の詳細については[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]を参照してください[Reporting Services 構成マネージャー &#40;del&#41; ](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)で、 [Reporting Services のドキュメント](http://go.microsoft.com/fwlink/?linkid=121312)msdn.microsoft.com します。  
  
  
##  <a name="SampleDatabases"></a> SQL Server サンプル データベース  
 Adventure Works ファミリのサンプル データベースは、レポート作成の学習用やサンプル レポート作成用のデータとしてお使いいただけます。  
  
 これらのデータベースには次のバージョンがあります。  
  
-   Adventure Works OLTP データベースは、架空の自転車メーカー (Adventure Works Cycles) 用のオンライン トランザクション処理の標準的なシナリオをサポートします。 シナリオには、製造、販売、購買、製品管理、連絡先管理、および人事があります。  
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベースは、データ ウェアハウスを構築する方法を示します。  
  
-   [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] プロジェクトは、ビジネス インテリジェンスのシナリオ用の AS データベースを構築するために使用できます。  
  
 サンプル データベースは付属しない[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]をインストールすると、インストールされていないと[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]またはレポート ビルダーのスタンドアロン バージョンです。 サンプル データベースは、 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843)からダウンロードしてください。 サンプル データベースのすべてのバージョンが一緒にダウンロードされます。 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、および [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] と共にリリースされた以前のバージョンのデータベースをダウンロードすることもできます。  
  
 前提条件とダウンロードとインストールに関する手順については、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]サンプル データベースは、「 [SQL Server 2008 サンプル データベースのインストール前提条件](http://go.microsoft.com/fwlink/?LinkId=166648)と[サンプル データベースのインストール](http://go.microsoft.com/fwlink/?LinkId=166649) CodePlex でします。  
  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 レポート ビルダーのインストール方法とアンインストール方法について説明しているトピックの一覧を次に示します。  
  
 [レポート ビルダーのスタンドアロン バージョンをインストール&#40;レポート ビルダー&#41;](install-windows/install-report-builder.md)  
  
 [レポート ビルダーのスタンドアロン バージョンをアンインストール&#40;レポート ビルダー&#41;](install-windows/uninstall-report-builder.md)  
  
 [レポート ビルダーの起動&#40;レポート ビルダー&#41;](report-builder/start-report-builder.md)  
  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  
