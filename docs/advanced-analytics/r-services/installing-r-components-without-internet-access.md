---
title: "インターネットへのアクセスなしで R コンポーネントをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 21
---
# インターネットへのアクセスなしで R コンポーネントをインストールする
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で使用する R コンポーネントのセットアップには、Microsoft ダウンロード センターまたは信頼できる別のサイトに用意されているファイルにアクセスするためのインターネット接続が必要です。 ただし、このトピックの説明に従ってローカル コピーを作成することで、インターネットにアクセスせずに、これらのコンポーネントをサーバーにインストールできます。  
  
  > [!TIP]
  > 
  > オフライン インストール プロセスの詳細なチュートリアルについては、[SQL Server Customer Advisory チーム](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)のこのブログを参照してください。
  
## <a name="installation-on-computers-with-no-internet-access"></a>インターネットにアクセスできないコンピューターでのインストール  
 オフライン インストールの実行時、R の必須コンポーネントのインストール用のリンクに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] はアクセスできません。 この問題を回避するには、インストーラーのコピーをローカルにダウンロードし、このドキュメントの説明に従ってセットアップを完了してください。
 
 R コンポーネントには、Microsoft R Open と Microsoft R Server という 2 つのインストーラーがあります。 SQL Server R Services を使用するには、この両方をダウンロードしてインストールする必要があります。 SQL Server セットアップ ウィザードを使用すると、正しい順序でインストールされます。


リリース  |ダウンロード リンク  
---------|---------
**SQL Server 2016 RTM**     |           
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)     
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)      
**SQL Server 2016 CU 1**     |           
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)     
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)      
**SQL Server 2016 CU 2**     |           
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)     
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)  
**SQL Server 2016 CU 3**     |           
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab: ](https://go.microsoft.com/fwlink/?LinkId=831785)     
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |           
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)     
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)  
**SQL Server 2016 SP 1 GDR**     |           
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)     
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)  

  
**オフライン インストールで R コンポーネントを更新する方法**     

1. 上記のリンクで、適切なバージョンをダウンロードします。
2. 更新プログラムをインストールするコンピューターのフォルダーに CAB ファイルをコピーします。
3. SQL Server のセットアップ ウィザードを実行し、Microsoft R ライセンス ページの [**同意**] をクリックします。  ダイアログ ボックスが開き、ダウンロード リンクの一覧が表示されます。 ダウンロードしたファイルの場所のパスを入力します。 
4. **[次へ]** をクリックすると、コンポーネントが使用できることが表示されます。SQL Server セットアップ ウィザードを完了します。
5. 必要に応じて、オープン ソース コンポーネントのアーカイブされたソース コードをダウンロードすることもできます。 詳細については、「[SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」を参照してください。


> [!IMPORTANT] インターネットに接続して SQL Server のセットアップ ウィザードを実行し、コンピューターに .cab ファイルをダウンロードすると、ローカルの言語が検出され、インストーラーの言語が自動的に変更されます。 
> 
> 一方、インターネットに接続接続にローカライズされたバージョンの SQL Server のいずれかをコンピューターにインストールし、R インストーラーをローカル共有にインストールする場合、ダウンロードしたファイルの名前を手動で編集し、インストールする言語の正しい言語識別子を挿入する必要があります。 
> 
> たとえば、日本語バージョンの SQL Server をインストールする場合、ファイル名を SRS_8.0.3.0_1033.cab から SRS_8.0.3.0_1041.cab に変更します。    
 
  
## <a name="see-also"></a>参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [R Services のセットアップのトラブルシューティング](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  