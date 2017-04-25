---
title: "SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "ssms のインストール、ssms のダウンロード、最新の ssms"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- "sql management studio インストール"
- "ダウンロード sql management studio"
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cc827737cec19c11d2102f968dc2b8bc638bda86
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のダウンロード
SQL Server Management Studio (SSMS) は、SQL Server のすべてのコンポーネントを構成、管理、開発し、それらのコンポーネントへアクセスできるようにする統合環境です。 SSMS では、さまざまなグラフィック ツールと、機能の豊富な多くのスクリプト エディターが用意されており、これらを使用して、あらゆるスキル レベルの開発者や管理者が SQL Server にアクセスできます。 このリリースでは、以前のバージョンの SQL Server との互換性が強化され、スタンドアロン Web インストーラーを利用できるようになり、新しいリリースが入手可能になると SSMS 内でトースト通知が表示されるようになります。  

    
| ![download](../ssdt/media/download.png) SQL Server Management Studio (SSMS) のダウンロード  |  |
|:---|:---|
|**[SQL Server Management Studio のダウンロード (16.5.3)](https://go.microsoft.com/fwlink/?LinkID=840946)**|運用環境向けの現在のリリース。|
|**[SQL Server Management Studio - リリース候補 (17.0 RC3) のダウンロード](../ssms/sql-server-management-studio-ssms-release-candidate.md)**|SQL Server vNext CTP1.3 のサポートが含まれており、16.x とサイド バイ サイドで動作しますが、実稼働用には推奨されません。| 


> [!NOTE]
> SSMS のリリースは、毎月ではありませんが番号が付けられるようになりました。 SSMS は無料です。 インストールと使用のためのライセンスは不要です。  


## <a name="sql-server-management-studio"></a>[SQL Server Management Studio]   
**バージョン情報**  
  
リリース番号: 16.5.3  
このリリースのビルド番号: 13.0.16106.4
  
**サポートされる SQL Server のバージョン**  
  
* このバージョンの SSMS は、すべての [サポート対象バージョンの SQL Server (SQL Server 2008 から SQL Server 2016)](https://support.microsoft.com/en-us/lifecycle?C2=1044) と連携し、Azure SQL Database および Azure SQL Data Warehouse で最新のクラウド機能と連携するための最大レベルのサポートを提供します。  
* SQL Server 2000 または SQL Server 2005 に対して明示的なブロックはありませんが、一部の機能が適切に機能しない可能性があります。  
* さらに、1 つの SSMS 16.x リリースまたは SSMS 2016 を、SSMS 2014 以前のバージョンと共にインストールできます。 
  
**サポートされるオペレーティング システム**  
  
SSMS の今回のリリースでは、最新の Service Pack を使用した次のプラットフォームがサポートされます。   
 Windows 10、Windows 8、Windows 8.1、Windows 7 (SP1)、Windows Server 2012 (64 ビット)、Windows Server 2012 R2 (64 ビット)、Windows Server 2008 R2 (64 ビット)  
   
 **使用できる言語**  
> [!NOTE]  
> SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。 
  
 SSMS の今回のリリースは、次の言語でインストールできます。  
[中国語 (中華人民共和国)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [中国語 (台湾)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [英語 (米国)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [フランス語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)  
[ドイツ語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [イタリア語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [日本語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [韓国語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [ポルトガル語 (ブラジル)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [ロシア語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [スペイン語](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)  

 
## <a name="changelog"></a>変更ログ  

16.5.3

このリリースでは次の問題が修正されました。

* SSMS 16.5.2 で、テーブルに複数のスパース列がある場合に 'Table' ノードが拡張される原因となっていた問題が修正されました。

* ユーザーは、SSIS カタログに、Microsoft Dynamics AX/CRM Online のリソースに接続される OData 接続マネージャーを含む SSIS パッケージを展開できます。 詳細については、「[OData 接続マネージャー](https://msdn.microsoft.com/library/dn584133.aspx)」を参照してください。

* 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects) を参照)。

* 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work) を参照)。

* データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors) を参照)。

* Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。

* *[最近使用した項目を開く]* メニューに、最近保存したファイルが表示されない ( [Connect ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files) を参照)。

* テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 [Connect ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection) を参照)。
 
* SQL デザイナーのスクロール バーの問題が修正されました ( [Connect ID 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016) を参照)。

* テーブルのコンテキスト メニューがすぐにハングする。 
 
* SSMS で利用状況モニターの例外がスローされ、クラッシュする場合がある ( [Connect ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/) を参照)。

* ".NET ランタイムの内部エラーにより、処理が中止されました。IP 71AF8579 (71AE0000)、終了コード 80131506" という内容のエラーで SSMS 2016 がクラッシュする。





全機能の一覧については、次をご覧ください   
                [SQL Server Management Studio - Changelog (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
  
既知の問題と回避策の一覧については、次をご覧ください   
                [SQL Server Management Studio - リリース ノート](../ssms/sql-server-management-studio-release-notes.md)  
  
ユーザー データの収集については、次をご覧ください   
                [SQL Server のプライバシーに関する声明](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx)。  
  
## <a name="previous-releases"></a>以前のリリース  
[SQL Server Management Studio の以前のリリース](../ssms/previous-sql-server-management-studio-releases.md)  
  
## <a name="feedback"></a>フィードバック  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)。  
  
## <a name="see-also"></a>参照  
[チュートリアル: SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[SQL Server Management Studio のドキュメント](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)  



