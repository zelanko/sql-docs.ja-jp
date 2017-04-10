---
title: "Azure で R Server Only SQL Server 2016 Enterprise VM を準備する | Microsoft Docs"
ms.custom: ""
ms.date: "12/22/2016"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# Azure で R Server Only SQL Server 2016 Enterprise VM を準備する

Azure の R Server Only SQL Server 2016 Enterprise Virtual Machine は、R ソリューションをサポートするサーバー環境をすばやく簡単に構成できる新しいオプションです。 この Azure 仮想マシンは Microsoft R Server (スタンドアロン) で事前に構成されています。 

この新しい仮想マシンは、Azure Marketplace で以前にリリースされていた RRE for Windows Virtual Machine の置き換えです。 

この仮想マシンには、アプリケーションとバックエンド システム内の R 分析を展開するための DeployR Enterprise も含まれています。 詳細については、「[About DeployR](https://msdn.microsoft.com/microsoft-r/deployr-about)」(DeployR の概要) を参照してください。


## R Server Virtual Machine を準備する

Azure VM を初めて使用する場合、ポータルの使用と仮想マシンの構成の詳細については、次の記事を参照してください。
[Virtual Machines - 作業の開始](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)

Microsoft Azure Marketplace から R Server VM を作成するには 
1. **[Virtual machines]** をクリックし、検索ボックスに「*R Server*」と入力します。
2. **[R Server Only SQL Server 2016 Enterprise]** を選択します。
3. 引き続き仮想マシンを準備するには、[https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/) の記事を参照してください。 
7. VM を作成して実行したら、**[接続]** ボタンをクリックして接続を開き、新しいコンピューターにログインします。
8. 接続すると、既定で**サーバー マネージャー**が開きますが、追加のサーバー構成は必要ありません。 **サーバー マネージャー**を閉じてデスクトップに戻り、次の手順に進んでください。
    + その他の R ツールまたは開発ツールのインストール
    + DeployR の構成  

Azure クラシック ポータルで R Server VM を検索するには
1. **[Virtual Machines]** をクリックし、**[新規]** をクリックします。
2. **[Compute]** と **[Virtual Machine]** が選択された状態で **[新規]** ペインが表示されます。 
3. **[ギャラリーから]** をクリックして VM イメージを探します。 検索ボックスに「*R Server*」と入力するか、**[Microsoft]** をクリックして、**[R Server Only SQL Server 2016 Enterprise]** が表示されるまで下にスクロールします。


## R ツールをインストールする
Microsoft R Server の既定では、R の基本インストールでインストールされるすべての R ツール (RTerm、RGui など) が含まれています。 R をすぐに使用し始める場合、RGui のショートカットはデスクトップに追加されています。

ただし、RStudio、R Tools for Visual Studio、Microsoft R Client など、その他の R ツールをインストールすることもできます。 ダウンロード場所と手順については、次のリンクを参照してください。
+ [R Tools for Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio for Windows](https://www.rstudio.com/products/rstudio/download/)

これらのツールをインストールした後は、必ずツールを R Server ライブラリに示してください。

## 仮想マシンで DeployR を使用する

この VM にインストールされている DeployR インスタンスを使用するには、いくつかの追加手順が必要です。 

DeployR インスタンスを構成するには:

1. VM で **DeployR Administrator Utility** を開きます。
2. 「[Post Installation Steps](https://msdn.microsoft.com/microsoft-r/deployr-install-on-windows)」(インストール後の手順) を参照して、DeployR の管理者パスワードを設定します。
3. DeployR Web コンテキストを設定します。 詳細については、「[DeployR Admin Installation in the Cloud](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud)」(クラウドでの DeployR Admin のインストール) を参照してください。 
4. 「[Configuring Azure Endpoints](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#configuring-azure-endpoints)」(Azure エンドポイントの構成) を参照して、VM の適切なポートを開きます。 
4. 「[Updating the firewall](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#updating-the-firewall)」(ファイアウォールの更新) を参照して、Windows ファイアウォールを更新します。 

## Azure ストレージ アカウントでデータにアクセスする 

Azure ストレージ アカウントからデータを使用する必要がある場合、データのアクセスまたは移動にはいくつかの選択肢があります。


+ ストレージ アカウントのデータを [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only) などのユーティリティを使用してローカル ファイル システムにコピーします。 

+ ファイルをストレージ アカウントのファイル共有に追加し、そのファイル共有を VM のネットワーク ドライブとしてマウントします。  詳細については、「[Windows で Azure File Storage を使用する](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)」を参照してください。 

## Azure Data Lake Storage (ADLS) アカウントでデータを使用する

webHDFS を使用して HDFS ファイル システムの参照と同様の方法でストレージ アカウントを参照している場合、ScaleR を使用して ADLS ストレージからデータを読み取ることができます。  詳細については、こちらの[セットアップ ガイド](http://go.microsoft.com/fwlink/?LinkId=723452)を参照してください。

## リソース

Microsoft R のその他のドキュメントについては、MSDN ライブラリの「[R Server and Scale R](https://msdn.microsoft.com/microsoft-r)」(R Server と Scale R) を参照してください。  


R の全般的な情報については、次のリソースも参照してください。 
+ [DataCamp](http://www.datacamp.com) R の無料の初級および中級コースと、Revolution R を使用してビッグ データを操作するコースを提供しています。
+ [Stack Overflow](http://www.stackoverflow.com) R プログラミングと ML ツールに関する疑問がある場合にお勧めのサイトです。 
+ [Cross Validated](https://stats.stackexchange.com/) 機械学習の統計の問題に関する疑問がある場合にお勧めのサイトです。
+ [R Help メーリング リストのアーカイブ](https://www.r-project.org/mail.html) 履歴情報を入手したい場合にお勧めのサイトです。 
+ [MRAN Web サイト](https://mran.microsoft.com/documents/getting-started/) その他の R リソースが掲載されています。  

## 参照
[SQL Server R サービス](https://msdn.microsoft.com/library/mt604845.aspx)
