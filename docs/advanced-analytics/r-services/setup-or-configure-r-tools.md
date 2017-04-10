---
title: "セットアップまたは R ツールを構成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# セットアップまたは R ツールを構成します。
  Microsoft R サーバーは、基本のすべての R ライブラリ、スケールの R パッケージ、および R コードを開発し、テストする必要がある標準の R ツールを提供します。 ただし、専用 R 開発環境を使用する場合は、いくつかなど、使用可能な多くの無料ツールです。  
  
## <a name="basic-r-tools"></a>基本的な R ツール  
 Microsoft R Server のインストールでは、ツールのすべての標準的な R のでその他のツールは必要ないに含まれる、 *インストールの基本* R の既定でインストールされます。

-   **RTerm**: R スクリプトを実行するためのコマンド ライン ツール 
  
-   **RGui.exe**: R 向けの単純な対話型エディターコマンドラインの引数は、RGui.exe および RTerm 同じです。 
  
-   **RScript**: バッチ モードでスクリプトの R を実行するためのコマンド ライン ツールです。  

既定では、これらのツールは、次のフォルダにインストールされます。
- SQL Server 2016: `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64`  
- SQL Server vNext: `C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`  

> [!TIP]  
>  他に支援が必要でしょうか。 R ツールのドキュメントは setup フォルダーにあります: `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` し、[ `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`します。  
>   
>  または、同じオープン **RGui**, 、] をクリックして **ヘルプ**, 、オプションのいずれかを選択します。  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R クライアントは、無料でダウンロードできるように簡単に実行できる Microsoft R Server または SQL Server R Services R ソリューションを開発します。

通常 for Visual Studio は、RStudio R ツールなどのさまざまな R 開発環境をインストールし、R の実行可能ファイルとして Microsoft R クライアントを使用することを指定します。 これにより、フル アクセス RevoScaleR パッケージおよび Microsoft R Server の他の機能です。

スクリプトを実行する、書き込みまたはアドホックの R コードを実行して RGui と RTerm などの使い慣れたツールを使用することもできます。

[Microsoft R クライアントをインストールします。](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="a-namebkmkrtoolsa-r-tools-for-visual-studio"></a> R Tools for Visual Studio  

 使用するにあたっての利便性のため [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースでは、使用を検討して [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] 開発環境として。 [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] Visual Studio のすべてのエディションで動作する Visual Studio の無料アドインでです。 Visual Studio では、Python と f# の統合のサポートも提供します。  

詳細については、次を参照してください。 [VisualStudio.com](https://www.visualstudio.com/vs/rtvs/)します。

 インストールする方法について説明 [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] 、無料 Community エディションの Visual Studio を使用します。  
  
#### <a name="install-visual-studio"></a>Visual Studio のインストール  
  
1.  Visual Studio の無償の Community エディションがこのページからダウンロードできます: [Visual Studio Community](http://visualstudio.com/products/visual-studio-community-vs.aspx)  
  
2.  ダウンロードが完了したら、クリックして **実行** しインストールするコンポーネントを選択します。  
  
     カスタム セットアップを実行する場合は、Microsoft Web Developer コンポーネントが必要である注意してください。  
  
3.  選択、 **全般** しばらくの間に設定します。 インストールするときに [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], 、toption R 開発用にカスタマイズされたレイアウトを変更する必要があります。  

#### <a name="add-the-r-tools"></a>R ツールを追加します。

R、Python、およびその他の多くの言語での拡張機能は Visual Studio をインストールした後、 **オプション** メニュー。

4. メニュー バーからツールをクリックし、[ **拡張機能と更新プログラム**します。

5. インストールの終わりに近い R ツールは、コンピューターで利用できるかどうかは、Microsoft R クライアントに Microsoft R サーバーまたは R ランタイム R ランタイムを使用する開発環境を変更するをしている R ランタイムのバージョンを検出します。

セットアップで使用する場合、R Server ランタイムが検出されない場合することができます、手動でいつでも変更を使用して、 **オプション** メニュー。 詳細については、次を参照してください。 [、IDE の構成](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide)します。

## <a name="rstudio"></a>RStudio

RStudio を使用する場合は、RevoScaleR ライブラリを使用するこれらの追加手順を実行します。
- 必要なパッケージおよびライブラリを取得する Microsoft R Server または Microsoft R クライアントをインストールします。
- 適切な R ランタイムを使用して R パスを更新します。

詳細については、次を参照してください。 [、IDE の構成](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide)します。


## <a name="see-also"></a>参照  
 [スタンドアロン R サーバーを作成します。](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Microsoft R Server &#40; の概要スタンドアロンと #41 です。](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  