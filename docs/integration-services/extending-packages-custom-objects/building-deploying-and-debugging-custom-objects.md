---
title: "ビルド、配置、およびカスタム オブジェクトのデバッグ |Microsoft ドキュメント"
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
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99fdd71403b12cee8ba9f207890268cde2e1d450
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="building-deploying-and-debugging-custom-objects"></a>カスタム オブジェクトのビルド、配置、およびデバッグ
  カスタム オブジェクトのコードを記述した後[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、アセンブリをビルド、配置、およびに統合する必要があります[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナーは、パッケージで使用できるようにし、テストおよびデバッグします。  
  
##  <a name="top"></a>ビルド、配置、および Integration Services のカスタム オブジェクトのデバッグ」の手順  
 オブジェクトのカスタム機能は既に記述しました。 次に、オブジェクトをテストし、ユーザーが使用できるようにする必要があります。 そのための手順は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 用に作成できるカスタム オブジェクトのすべての種類でほぼ同じです。  
  
 ビルド、配置、およびテストする手順を以下に示します。  
  
1.  [サインオン](#signing)厳密な名前で生成されるアセンブリ。  
  
2.  [ビルド](#building)アセンブリ。  
  
3.  [展開](#deploying)移動するか、適切なにコピーすることにより、アセンブリ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]フォルダーです。  
  
4.  [インストール](#installing)グローバル アセンブリ キャッシュ (GAC) 内のアセンブリ。  
  
     オブジェクトは自動的にツールボックスに追加されます。  
  
5.  [トラブルシューティングを行う](#troubleshooting)必要に応じて、展開します。  
  
6.  [テスト](#testing)し、コードをデバッグします。  
  
 使えるようになりました SSIS デザイナー SQL Server Data Tools (SSDT) で作成、保守、およびの異なるバージョンを対象とするパッケージを実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 カスタム拡張機能でこの機能強化の影響に関する詳細については、次を参照してください[SQL Server 2016 用 SSDT 2015 の複数バージョンのサポートによってサポートされる SSIS カスタム拡張を取得する。](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/)  
  
##  <a name="signing"></a>アセンブリの署名  
 アセンブリを共有することを目的としている場合は、アセンブリをグローバル アセンブリ キャッシュにインストールする必要があります。 グローバル アセンブリ キャッシュに追加されたアセンブリは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] などのアプリケーションで使用できるようになります。 グローバル アセンブリ キャッシュの要件として、アセンブリに厳密な名前で署名する必要があります。これにより、アセンブリがグローバルに一意であることが保証されます。 厳密な名前が付けられたアセンブリは、アセンブリの名前、カルチャ、公開キー、およびバージョン番号を含む完全修飾名を持ちます。 ランタイムはこの情報を使用して、アセンブリを検索し、同じ名前の他のアセンブリと区別します。  
  
 アセンブリに厳密な名前で署名するには、公開キーと秘密キーのペアを保持しているか、または作成する必要があります。 この暗号化用の公開キーと秘密キーのペアがビルド時に使用され、厳密な名前のアセンブリが作成されます。  
  
 厳密な名前と、アセンブリへの署名に必要な手順の詳細については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK のドキュメントの次のトピックを参照してください。  
  
-   厳密な名前付きアセンブリ  
  
-   キー ペアの作成  
  
-   厳密な名前でのアセンブリへの署名  
  
 アセンブリには、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] でビルド時に厳密な名前を使用して簡単に署名できます。 **プロジェクト プロパティ**ダイアログ ボックスで、**署名**タブです。 オプションを選択して**アセンブリに署名**しキー (.snk) ファイルのパスを指定します。  
  
##  <a name="building"></a>アセンブリのビルド  
 プロジェクトに署名した後に、ビルドまたはで使用できるコマンドを使用して、プロジェクトまたはソリューションを再構築する必要があります、**ビルド**のメニュー[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]です。 ソリューションには、カスタム ユーザー インターフェイス用の独立したプロジェクトが含まれている場合があります。このプロジェクトにも厳密な名前で署名する必要があり、同時にビルドすることが可能です。  
  
 アセンブリの配置とグローバル アセンブリ キャッシュへのインストールを実行するための最も便利な方法は、これらの手順を [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] でビルド後のイベントとしてスクリプト処理することです。 提供されているビルド イベント、**コンパイル**のプロジェクト プロパティ ページ、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]プロジェクトとの間、**ビルド イベント**を c# プロジェクトのページです。 完全なパスがコマンド プロンプト ユーティリティなどの必要な**gacutil.exe**です。 スペースを含むパスと、スペースを含むパスに展開される $(TargetPath) などのマクロは、引用符で囲む必要があります。  
  
 カスタム ログ プロバイダーのビルド後に実行するコマンド ラインの例を次に示します。  
  
```  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)  
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\130\DTS\LogProviders "  
```  
  
##  <a name="deploying"></a>アセンブリの配置  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナーは、一連の時に作成されるフォルダー内のファイルを列挙することによりパッケージで使用できるカスタム オブジェクトを検索[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]がインストールされています。 ときに、既定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール設定を使用する、この一連のフォルダーが下にある**C:\Program files \microsoft SQL Server\130\DTS**です。 ただし、カスタム オブジェクトのセットアップ プログラムを作成する場合は、値を確認する必要があります、 **hkey_local_machine \software\microsoft\microsoft SQL Server\130\SSIS\Setup\DtsPath**レジストリ キーをこのフォルダーの場所を確認します。  
  
> [!NOTE]  
>  SQL Server Data Tools で複数バージョンのサポートでうまく機能するカスタム コンポーネントを展開する方法の詳細については、次を参照してください。 [SQL Server 2016 用 SSDT 2015 の複数バージョンのサポートによってサポートされる SSIS カスタム拡張を取得する](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/)です。  
  
 アセンブリをフォルダーに配置する方法は 2 つあります。  
  
-   コンパイル済みのアセンブリをビルド後に適切なフォルダーに移動またはコピーします  (ビルド後のイベントにコピー コマンドを含めると便利です)。  
  
-   適切なフォルダーでアセンブリを直接ビルドします。  
  
 次の配置フォルダー **C:\Program files \microsoft SQL Server\130\DTS**のカスタム オブジェクトのさまざまな種類で使用します。  
  
|カスタム オブジェクト|配置フォルダー|  
|-------------------|-----------------------|  
|タスク|処理手順|  
|[ODBC 入力先エディター]|接続|  
|ログ プロバイダー|LogProviders|  
|データ フロー コンポーネント|PipelineComponents|  
  
> [!NOTE]  
>  アセンブリは、使用可能なタスクや接続マネージャーなどの列挙をサポートするために、これらのフォルダーにコピーされます。 したがって、カスタム オブジェクトのカスタム ユーザー インターフェイスのみを含むアセンブリをこれらのフォルダーに配置する必要はありません。  
  
##  <a name="installing"></a>グローバル アセンブリ キャッシュにアセンブリをインストールします。  
 タスク アセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールするには、コマンド ライン ツールを使用して**gacutil.exe**、またはアセンブリをドラッグして、`%system%\assembly`ディレクトリ。 便宜上への呼び出しも含めることができます**gacutil.exe**でビルド後のイベントです。  
  
 次のコマンドは、という名前のコンポーネントをインストール*MyTask.dll*を使用して GAC に**gacutil.exe**です。  
  
 `gacutil /iF MyTask.dll`  
  
 カスタム オブジェクトの新しいバージョンをインストールしたら、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを閉じて再度開く必要があります。 グローバル アセンブリ キャッシュに以前のバージョンのカスタム オブジェクトをインストールしている場合は、新しいバージョンをインストールする前に以前のバージョンを削除する必要があります。 アセンブリをアンインストールするには、実行**gacutil.exe**アセンブリ名を指定し、`/u`オプション。  
  
 グローバル アセンブリ キャッシュの詳細については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ツールのグローバル アセンブリ キャッシュ ツール (Gactutil.exe) を参照してください。  
  
##  <a name="troubleshooting"></a>展開のトラブルシューティング  
 カスタム オブジェクトが表示された場合、**ツールボックス**または、使用可能なオブジェクトの一覧は、以下のパッケージに追加することはできません。  
  
1.  グローバル アセンブリ キャッシュにコンポーネントの複数のバージョンがないか検索します。 グローバル アセンブリ キャッシュにコンポーネントの複数のバージョンがある場合、デザイナーはコンポーネントを読み込めないことがあります。 アセンブリのすべてのインスタンスをグローバル アセンブリ キャッシュから削除し、アセンブリを再度追加してください。  
  
2.  配置フォルダーに存在するアセンブリのインスタンスが 1 つだけであることを確認します。  
  
3.  ツールボックスを更新します。  
  
4.  アタッチ[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]に**devenv.exe**例外が発生しないことを確認する初期化コードをステップ実行にブレークポイントを設定します。  
  
##  <a name="testing"></a>テストとコードのデバッグ  
 カスタム オブジェクトの実行時のメソッドをデバッグする最も簡単な方法では、開始**dtexec.exe**から[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]後、カスタム オブジェクトを構築し、コンポーネントを使用してパッケージを実行します。  
  
 など、コンポーネントのデザイン時のメソッドをデバッグする場合、**検証**メソッド、コンポーネントを使用して、2 番目のインスタンスにパッケージを開く[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]にアタッチし、 **devenv.exe**プロセスです。  
  
 パッケージを開きで実行されている場合は、コンポーネントの実行時のメソッドをデバッグする場合[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナーは、する必要があります強制的に、パッケージの実行を一時停止されるようにに添付することも、 **DtsDebugHost.exe**プロセスです。  
  
#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a>dtexec.exe にアタッチしてオブジェクトの実行時のメソッドをデバッグするには  
  
1.  デバッグ構成でプロジェクトへの署名とビルドを行い、プロジェクトを配置し、このトピックで説明したようにグローバル アセンブリ キャッシュにインストールします。  
  
2.  **デバッグ**のタブ**プロジェクトのプロパティ**を選択**外部プログラムの開始**として、**開始動作**、検索と**dtexec.exe**が既定では C:\Program files \microsoft SQL server \130\dts\binn でインストールされています。  
  
3.  **コマンド ライン オプション**テキスト ボックスで、**開始オプション**コンポーネントを使用するパッケージの実行に必要なコマンドライン引数を入力します。 多くの場合、コマンド ライン引数は /F[ILE] スイッチと、それに続く .dtsx ファイルのパスおよびファイル名で構成されます。 詳細については、「 [dtexec Utility](../../integration-services/packages/dtexec-utility.md)」を参照してください。  
  
4.  コンポーネントの実行時のメソッド内の適切な位置のソース コードに、ブレークポイントを設定します。  
  
5.  プロジェクトを実行します。  
  
#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a>SQL Server データ ツールにアタッチしてカスタム オブジェクトのデザイン時のメソッドをデバッグするには  
  
1.  デバッグ構成でプロジェクトへの署名とビルドを行い、プロジェクトを配置し、このトピックで説明したようにグローバル アセンブリ キャッシュにインストールします。  
  
2.  カスタム オブジェクトのデザイン時のメソッド内の適切な位置のソース コードに、ブレークポイントを設定します。  
  
3.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の 2 番目のインスタンスを開き、カスタム オブジェクトを使用するパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを読み込みます。  
  
4.  最初のインスタンスから[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の 2 つ目のインスタンスにアタッチ**devenv.exe**でを選択して、パッケージが読み込まれる**プロセスにアタッチする**から、**デバッグ**最初のインスタンスのメニュー。  
  
5.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の 2 番目のインスタンスからパッケージを実行します。  
  
#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a>SQL Server データ ツールにアタッチしてカスタム オブジェクトの実行時のメソッドをデバッグするには  
  
1.  前の手順に記載された手順が完了した後にアタッチできるように、パッケージの実行を一時停止を強制的**DtsDebugHost.exe**です。 ブレークポイントを追加することによってこの一時停止を強制することができます、 **OnPreExecute**イベント、またはプロジェクトにスクリプト タスクを追加して、モーダル メッセージ ボックスを表示するスクリプトを入力します。  
  
2.  パッケージを実行します。 一時停止が発生するのインスタンスに切り替える[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コード プロジェクトが選択し、開く**プロセスにアタッチする**から、**デバッグ**メニュー。 インスタンスにアタッチすることを確認**DtsDebugHost.exe**として表示されている**マネージ, x86**で、**型**列として表示されているインスタンスにない**x86**のみです。  
  
3.  一時停止したパッケージに戻ると、ブレークポイント以降続行またはをクリックして**OK**スクリプト タスクで発生したメッセージ ボックスを閉じ、パッケージの実行およびデバッグを続行します。  
  
## <a name="see-also"></a>参照  
 [Integration Services 用カスタム オブジェクトの開発](../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)   
 [カスタム オブジェクトの永続化](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [パッケージ開発のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
