---
title: "SQL Server Management Studio の以前のリリース | Microsoft Docs"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87f593c3-8b76-4c12-963a-31d35f2fb294
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 0927784589c1f7227b432ff49f81f29de20083ec
ms.openlocfilehash: 200753bf64d92043171788852227c6199b64711d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="previous-sql-server-management-studio-releases"></a>SQL Server Management Studio の以前のリリース
  
次に示す SQL Server Management Studio の以前のリリースが使用できます。
   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1653-releasehttpgomicrosoftcomfwlinklinkid840946"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 16.5.3 リリース](http://go.microsoft.com/fwlink/?LinkID=840946)

**バージョン情報**  
  
*SSMS の今回のリリースでは、Visual Studio 2015 の分離シェルを使用します。*  
リリース番号: 16.5.3  
このリリースのビルド番号: 13.0.16106.4

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



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-165-releasehttpgomicrosoftcomfwlinklinkid832812"></a>[SQL Server Management Studio 16.5 リリース](http://go.microsoft.com/fwlink/?LinkID=832812)の![ダウンロード](../ssdt/media/download.png)

**バージョン情報**  
  
*SSMS の今回のリリースでは、Visual Studio 2015 の分離シェルを使用します。*  
リリース番号: 16.5  
このリリースのビルド番号: 13.0.16000.28

**このビルドに関する既知の問題**  

1. 制約の確認時に Invoke-Sqlcmd で誤って複数の行が挿入されます。 [Microsoft Connect アイテム: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

2. 可用性グループの作成時に ENU 以外の言語バージョンが完全に動作しません。

3. クエリ プラン XML をクリックしたときに適切な SSMS UI が開きません。

**変更ログ**

* テーブル名に ";:" が含まれるデータベースをクリックするとクラッシュすることがあるという問題を修正しました。
* [AS Tabular Database Properties] (AS 表形式データベースのプロパティ) ウィンドウの [モデル] ページに変更を加えると、元の定義がスクリプト出力されるという問題を修正しました。 
[Microsoft Connect アイテム: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* [最近使ったファイル] の一覧に一時ファイルが追加されるという問題を修正しました。  
[Microsoft Connect アイテム: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* オブジェクト エクスプローラー ツリーのユーザー テーブル ノードで、[圧縮の管理] メニュー項目が無効になるという問題を解決しました。  
[Microsoft Connect アイテム: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* オブジェクト エクスプローラー、登録済みサーバー エクスプローラー、およびテンプレート エクスプローラーのフォントサイズ、およびエクスプ ローラーの詳細をユーザーが設定できないという問題を解決しました。 エクスプローラーのフォントには、環境フォントが使用されます。  
[Microsoft Connect アイテム: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* 接続が失われると、SSMS は常に既定のデータベースに再接続するという問題を解決しました。  
[Microsoft Connect アイテム: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* 実行プラン アイコンを含む、ポリシー管理およびクエリ エディター ウィンドウで、多くの高 DPI 問題を修正しました。

* 拡張イベントのフォントと色を構成するためのオプションが見つからないという問題を修正しました。

* アプリケーションを閉じるとき、またはエラー ダイアログ ボックスが表示されるときに発生する SSMS のクラッシュの問題を修正しました。


   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1641-september-2016-releasehttpgomicrosoftcomfwlinklinkid828615"></a>[SQL Server Management Studio 16.4.1 (2016 年 9 月) リリース](http://go.microsoft.com/fwlink/?LinkID=828615)の![ダウンロード](../ssdt/media/download.png)

**バージョン情報**  
  
*SSMS の今回のリリースでは、Visual Studio 2015 の分離シェルを使用します。*  
リリース番号: 16.4.1  
このリリースのビルド番号: 13.0.15900.1
  
**このビルドに関する既知の問題**  

1. **Active Directory ユニバーサル認証を使用して SSMS インスタンス用にログインできる Azure Active Directory アカウントは 1 つだけです。**  
    この制限は、Active Directory ユニバーサル認証に限定されます。Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証を使用して別のサーバーにログインできます。
    
    回避策としては、別の SSMS インスタンスを使用して、別の Azure Active Directory アカウントとしてログインしてください。 
    
2. **SSMS でのデータ層アプリケーション フレームワーク (DacFx) コマンドおよびスキーマ デザイナーでは、Active Directory ユニバーサル認証はサポートされていません。**  
    SSMS での DacFx を使用するコマンド (例: インポートおよびエクスポート) 、 スキーマ デザイナーでは、現在 Active Directory ユニバーサル認証はサポートされていません。
    
    回避策としては、Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証など、SSMS で提供される認証の他の形式を使用してください。

3. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。**  
    以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
    
    この問題の回避策としては、 [SSIS インスタンスと連携された SSMS リリース](../ssms/previous-sql-server-management-studio-releases.md)を使用して、SQL Server Integration Service インスタンスに接続してください。 
  
4. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。**  
    これは将来に対応する既知の制限です。 それまでは、 [SSMS 2014 リリース](../ssms/previous-sql-server-management-studio-releases.md) を使用して、メンテナンス プランを保存してください。  
    
5. **英語以外の SSMS のインストールには、追加のセキュリティ パッケージのインストールが必要になる場合があります。**  
SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。
  
6. **SQL Server 構成マネージャーは、SQL Server がクライアント コンピューターにインストールされていない場合は起動できません。**  
    SQL server がクライアント コンピューターにインストールされておらず、SQL Server 構成マネージャーを起動する場合は、次のエラーが表示されます。   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加している場合は、次の手順に従います。  
        1. SSMS の '登録済みサーバー’ ビューに移動します。  
        2. 構成する SQL Server インスタンスを右クリックします。  
        3. 右クリックで表示されるメニューで、'SQL Server 構成マネージャー...' を選択します 。    
          
      * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加していない場合は、次の手順に従います。  
        1. 管理者としてコマンド プロンプトを開きます。  
        2. 次のコマンドを使用して、Mofcomp ツールを実行します。  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Mofcomp ツールを実行した後、次のコマンドを実行して、WMI サービスを再起動し、変更を有効にします。  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

 
**変更ログ** 

*  ストアド プロシージャの ALTER/変更を実行しようとすると失敗するという問題を修正しました。  
[Microsoft Connect アイテム #3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* PowerShell でデータの表示や書き込みを行うための新しいコマンドレット 'Read-SqlTableData'、'Read-SqlViewData'、'Write-SqlTableData'。  
[Trello Read-SqlTableData カード](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Microsoft Connect アイテム #2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* 新しい 'Add-SqlLogin' コマンドレット。PowerShell を使った新しいログイン管理シナリオを可能にします。  
[Microsoft Connect アイテム #2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  さまざまな国のクラウドに接続するユーザーのためのサポートと使いやすさが向上しています。
    
*  メモリ不足例外がスローされるという問題を修正しました。  
[Microsoft Connect アイテム #3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Microsoft Connect アイテム #3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  スキーマによるフィルター処理というフィルター オプションを選択できないという問題を修正しました。  
[Microsoft Connect アイテム #3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Microsoft Connect アイテム #3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  ストレッチ データベースのモニター ウィンドウにアクセスできないという問題を修正しました。
    
*  F1 ヘルプで常にオンライン コンテンツが開くという問題を修正しました。 オンラインとオフラインのどちらのヘルプを参照するかを、[ヘルプ] メニューの "ヘルプ設定の設定" で選べるようになりました。   
[Microsoft Connect アイテム #2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  1200 レベルの Analysis Services 表形式モデルをスクリプト化するときに、パスワードがスクリプト用に除去されない (サーバー バージョンでは除去されていても) という問題を解決しました (クライアント モデル オブジェクトはスクリプト化の前に同期されるようになりました)。
    
*  'SELECT TOP N ROWS' オプションを選択すると、TOP 演算子について非推奨の構文が生成されるという問題を修正しました。  
[Microsoft Connect アイテム #3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  SSMS のさまざまなレイアウトの問題を修正しました。たとえば、[ログインのプロパティ] ページや詳細設定クエリ実行オプションです。   
[Microsoft Connect アイテム #3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  ユーザーが新しいクエリ ウィンドウを開くたびにソリューションが自動的に作成されるという問題を修正しました。   
[Microsoft Connect アイテム #2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Microsoft Connect アイテム #2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Microsoft Connect アイテム #2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  オブジェクト エクスプローラーでシステム データベースの中のテンポラル テーブルを拡張できないという問題を修正しました。  
[Microsoft Connect アイテム #2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  SSMS が SELECT @@trancount というクエリをバッチ実行後に実行するという問題を修正しました。    
[Microsoft Connect アイテム #3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Analysis Services でスクリプトをサーバーのプロパティ ページから作成すると接続ダイアログが非表示になるという問題を修正しました。
    
*  Ctrl + Q キーを押してもクイック起動ツール バーが選択されないという問題を修正しました。
    
*  データベースの MaxSize を [サーバーのプロパティ] ダイアログで変更するときにデータベースが 2 TB を超えていると中断されるという問題を修正しました。  
[Microsoft Connect アイテム #1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  データベースの復元ウィザードで、先頭にホワイトスペースのあるファイル名が受け付けられないという問題を修正しました。   
[Microsoft Connect アイテム #2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)

*  データベースの復元ウィザードで、先頭にホワイトスペースのあるファイル名が受け付けられないという問題を修正しました。   
[Microsoft Connect アイテム #2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-163-august-2016-releasehttpgomicrosoftcomfwlinklinkid824938"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 16.3 (2016 年 8 月) リリース](http://go.microsoft.com/fwlink/?LinkID=824938)
 2016 年 8 月 15 日 | バージョン番号: 13.0.15700.28

**機能**  
1. 新しい認証オプションの "Active Directory ユニバーサル認証"
2. SQL Server PowerShell モジュール用の新しいコマンドレット
3. データベース エンジン チューニング アドバイザー (DTA) と拡張イベント テンプレートの改善
4. ベータ版での [SSMS の高解像度表示](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)のサポート

[機能の詳細については、SSMS の変更ログをご覧ください。](../ssms/sql-server-management-studio-changelog-ssms.md)

**既知の問題**

このリリースの SQL Server Management Studio に関連する問題と制約を次に示します。  

1. **Active Directory ユニバーサル認証を使用して SSMS インスタンス用にログインできる Azure Active Directory アカウントは 1 つだけです。**  
    この制限は、Active Directory ユニバーサル認証に限定されます。Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証を使用して別のサーバーにログインできます。
    
    回避策としては、別の SSMS インスタンスを使用して、別の Azure Active Directory アカウントとしてログインしてください。 
    
2. **SSMS でのデータ層アプリケーション フレームワーク (DacFx) コマンドおよびスキーマ デザイナーでは、Active Directory ユニバーサル認証はサポートされていません。**  
    SSMS での DacFx を使用するコマンド (例: インポートおよびエクスポート) 、 スキーマ デザイナーでは、現在 Active Directory ユニバーサル認証はサポートされていません。
    
    回避策としては、Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証など、SSMS で提供される認証の他の形式を使用してください。

3. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。**  
    以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
    
    この問題の回避策としては、 [SSIS インスタンスと連携された SSMS リリース](../ssms/previous-sql-server-management-studio-releases.md)を使用して、SQL Server Integration Service インスタンスに接続してください。 
  
4. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。**  
    これは将来に対応する既知の制限です。 それまでは、 [SSMS 2014 リリース](../ssms/previous-sql-server-management-studio-releases.md) を使用して、メンテナンス プランを保存してください。  
    
5. **英語以外の SSMS のインストールには、追加のセキュリティ パッケージのインストールが必要になる場合があります。**  
SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。
  
6. **SQL Server 構成マネージャーは、SQL Server がクライアント コンピューターにインストールされていない場合は起動できません。**  
    SQL server がクライアント コンピューターにインストールされておらず、SQL Server 構成マネージャーを起動する場合は、次のエラーが表示されます。   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加している場合は、次の手順に従います。  
        1. SSMS の '登録済みサーバー’ ビューに移動します。  
        2. 構成する SQL Server インスタンスを右クリックします。  
        3. 右クリックで表示されるメニューで、'SQL Server 構成マネージャー...' を選択します 。    
          
      * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加していない場合は、次の手順に従います。  
        1. 管理者としてコマンド プロンプトを開きます。  
        2. 次のコマンドを使用して、Mofcomp ツールを実行します。  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Mofcomp ツールを実行した後、次のコマンドを実行して、WMI サービスを再起動し、変更を有効にします。  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  


**修正**
1. SSMS で、復号化された AlwaysEncrypted ラージ オブジェクト (LOB) 列のクリア テキストを表示するようバグを修正 (Microsoft Connect アイテム #2413024)。
2. Windows の視覚スタイルが有効でない場合のクラッシュを解決するよう [Always Encrypted] ダイアログボックスのバグを修正。
3. SQL Server インスタンスへの接続を妨げる 'メソッドが見つかりませんでした' エラーのバグを修正。
4. datetimeoffset を含むパーティション関数を作成するときの SSMS クラッシュのバグを修正。
5. Distributed Replay 管理ツール (DReplay.exe) を起動するための Microsoft .NET 3.5 の要件を削除するようバグを修正。
6. サーバーの完全修飾名をサポートするよう [Analysis Services 配置] ウィザードのバグを修正。
7. SSMS で、2016 互換性モデルの Analysis Services 表形式モデルでパーティションを表示するようバグを修正 (Microsoft Connect アイテム #2845053)。

[修正の詳細については、SSMS の変更ログをご覧ください。](../ssms/sql-server-management-studio-changelog-ssms.md)
 
---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-july-2016-hotfix-update-releasehttpgomicrosoftcomfwlinklinkid822301"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 2016 年 7 月修正プログラム リリース](http://go.microsoft.com/fwlink/?LinkID=822301)

2016 年 7 月 13 日 | バージョン番号: 13.0.15600.2

**機能**  
1. SSMS での Azure SQL Data Warehouse のサポート。   
2. SQL Server PowerShell モジュールの大幅な更新。   
3. Azure SQL データベースへの接続時間を大幅に短縮。  
4. Analysis Services プロセス ダイアログなどの、表形式データベース向けの SQL Server 2016 (互換性レベル 1200) のサポートを強化。   

[詳細な情報および利用可能な機能については、SSMS 変更ログをご覧ください。](../ssms/sql-server-management-studio-changelog-ssms.md)

**既知の問題** 
1. **SSMS 7 月の修正プログラム リリースのインストーラーが SSMS 年 8 月のリリースとして表示されます。**
7 月の修正プログラムのセットアップ ページでは、内部のビルド設定により、8 月と記載されています。 このパッケージは、実際には SSMS 7 月のリリースの更新プログラムです。 
2. **SSMS は、'2016 年 7 月修正プログラム' リリースをインストールした後、SQL Server インスタンスに接続できません。**
マイクロソフトは、SSMS の最新の更新プログラムで、サーバーに接続しようとすると次のエラー メッセージが表示されるという問題を認識しています。 
   ```
    "Method not found: 'Void Microsoft.SqlServer.Management.Common.SqlConnectionInfo.set_ApplicationIntent(System.String)'"
    ```
  
    この問題の修正は、SSMS の次のリリースで適用されます。 この問題の回避策としては、SSM をアンインストールして再インストールします。 詳細については、 [この問題に関する Microsoft Connect のスレッドを参照してください](https://connect.microsoft.com/SQLServer/feedback/details/2925257/not-able-to-connect-to-sql-server-instances-after-installing-ssms-2016-july-update)。
    
3. **Azure ストレージ アカウントを選択しようとすると、SSMS がクラッシュします。**
SSMS の 7 月リリースおよび 7 月の修正リリースでは、Azure ストレージ アカウントを選択して、'クラシック' のストレージ アカウントを持っていない場合、SSMS がクラッシュします。
この問題の修正は、今後の SSMS のリリースで適用されます。 この問題の回避策としては、クラシック ストレージ アカウントを作成するか、 [T-SQL を使用してバックアップまたは復元](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx)を実行して、Azure ストレージ アカウントにデータベースをバックアップ/復元します。

4. **SSMS のバックアップ/復元ウィザードで、'クラシック' の Azure ストレージ アカウントしか表示されません。**
SSMS の 7 月リリースおよび 7 月の修正プログラム リリースでは、バックアップまたは復元のウィザードを使用してバックアップまたは復元しようとすると、新しい資格情報の作成で 'クラシック' の Azure ストレージ アカウントしか表示されません。
この問題の修正は、今後の SSMS のリリースで適用されます。 この問題の回避策として、 [T-SQL を使用してバックアップまたは復元](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx)を実行して、使用可能な Azure 'クラシック' ストレージ アカウントにデータベースをバックアップ/復元するか、’ARM タイプ’ のストレージ アカウントにバックアップします。 

5. **英語以外の SSMS のインストールには、追加のセキュリティ パッケージのインストールが必要になる場合があります。**
SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。
6. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。** 以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
この問題の回避策としては、SSIS インスタンスと連携された SSMS リリースを使用して、SQL Server Integration Service インスタンスに接続してください。
7. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。** マイクロソフトはこの問題の解決に向けて取り組んでいます。 それまでは、SSMS 2014 以前のリリースを使用して、メンテナンス プランを保存してください。
8. **SQL Server 構成マネージャーは、SQL Server がクライアント コンピューターにインストールされていない場合は起動できません。** SQL server がクライアント コンピューターにインストールされておらず、SQL Server 構成マネージャーを起動する場合は、'WMI プロバイダーに接続できません' というエラーが表示されます。 以下の回避策があります。
    * 管理者としてコマンド プロンプトを開きます。
    * 次のコマンドを使用して、Mofcomp ツールを実行します。  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Mofcomp ツールを実行した後、次のコマンドを実行して、WMI サービスを再起動し、変更を有効にします。  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**修正**  
1. ユーザーが SELECT 権限を持っていない場合に、SSMS クエリ デザイナーにテーブルを追加できるようバグを修正。
2. 'TRY_CAST()' と 'TRY_CONVERT()' 関数の IntelliSense サポートを追加するためのバグを修正 [(Microsoft Connect アイテム #2453461)](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast)。
3. ドラッグ アンド ドロップで Sql ファイルを開くことができるよう、SSMS のエディター ウィンドウのバグを修正 [(Microsoft Connect アイテム #2690658)](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios)。
4. 多次元の Analysis Services モデルのデータ フィード プロバイダーが正しく示されるよう、Analysis Services のバグを修正。
5. SSMS テーブル デザイナーでの結合のリンクを編集しようとする際のクラッシュを防ぐよう、SSMS のバグを修正 [(Microsoft Connect アイテム #2721052)](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms)。  

[詳細な情報および利用可能なバグの修正については、SSMS 変更ログをご覧ください。](../ssms/sql-server-management-studio-changelog-ssms.md)

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-june-2016-releasehttpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 2016 年 6 月リリース](http://go.microsoft.com/fwlink/?LinkID=799832)

2016 年 6 月 1 日 | バージョン番号: 13.0.15000.23

**機能**  
簡素化された新しい SSMS インストーラー。 スタンドアロンの SSMS リリース。 自動的な更新プログラムの確認。 新しいクイック検索ダイアログ。 Visual Studio 2015 シェルなどを基にして構築された SSMS。   
[詳細については、SSMS 変更ログをご覧ください。](../ssms/sql-server-management-studio-changelog-ssms.md)

**既知の問題** 
1. **現在、Always Encrypted ウィザードからの PowerShell スクリプトの生成は無効です。**
この問題の修正は、次回の毎月の SSMS 更新プログラムで使用できます。
2. **Azure SQL Database に接続した場合、オブジェクト エクスプ ローラーの [列の暗号化] コンテキスト メニュー項目がテーブルと列に対して無効です。** この問題の修正は、次回の毎月の SSMS 更新プログラムで使用できます。 この問題を回避するには、オブジェクト エクスプ ローラーでデータベースを右クリックし、[タスク] を選択して [列の暗号化] を選択し、Azure SQL Database の列とテーブルを暗号化します。
3. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。** 以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
この問題の回避策としては、SSIS インスタンスと連携された SSMS リリースを使用して、SQL Server Integration Service インスタンスに接続してください。
4. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。** マイクロソフトはこの問題の解決に向けて取り組んでいます。 それまでは、SSMS 2014 以前のリリースを使用して、メンテナンス プランを保存してください。
5. **SQL Server 構成マネージャーは、SQL Server がクライアント コンピューターにインストールされていない場合は起動できません。** SQL server がクライアント コンピューターにインストールされておらず、SQL Server 構成マネージャーを起動する場合は、'WMI プロバイダーに接続できません' というエラーが表示されます。 以下の回避策があります。
    * 管理者としてコマンド プロンプトを開きます。
    * 次のコマンドを使用して、Mofcomp ツールを実行します。  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Mofcomp ツールを実行した後、次のコマンドを実行して、WMI サービスを再起動し、変更を有効にします。  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**修正**  
1. 現在のドキュメントへの統合が強化され、正規表現を使用した検索が可能な SSMS のクイック検索ダイアログ ([Microsoft Connect アイテム #2735513](https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/))。
2. ヘルプ ドキュメントおよび記事を正しく表示できるよう、SSMS の状況依存の F1 ヘルプのバグを修正。
3. スクロール時に SSMS のクラッシュの原因となるクエリ データ ストア '低下したクエリ' ビューのバグを修正。
4. Excel 2016 から SQL Server Analysis Services への接続を許可するよう、Excel Analysis Services OLEDB コネクタのバグを修正。
5. マルチ モニター システムで、SSMS のメイン ウィンドウと同じのモニターに [接続] ダイアログ ボックスを表示するよう、SSMS の [接続] ダイアログ ボックスのバグを修正 ([Microsoft Connect アイテム #724909)](https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/)。
6. Always Encrypted エクスペリエンスのバグを修正。 Always Encrypted メニュー オプションが Stretch Database に対して正しく有効にならないバグを修正しました。 また、SafeNet (Luna SA) HSM プロバイダーを正しく使用しない Always Encrypted ウィザードのバグも修正しました。

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2014-sp1httpdownloadmicrosoftcomdownload156156992e6-f7c7-4e55-833d-249bd2348138enux86sqlmanagementstudiox86enuexe"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 2014 SP1](http://download.microsoft.com/download/1/5/6/156992E6-F7C7-4E55-833D-249BD2348138/ENU/x86/SQLManagementStudio_x86_ENU.exe)

2015 年 5 月 14 日 | バージョン番号: 12.0.4100.1

**機能**  
管理ポータル メニューでの新しいオープン操作やテーブル デザイナー統合などで、Azure SQL Database のサポートを強化。   
[詳細については、リリース ノートをご覧ください](https://support.microsoft.com/en-us/kb/3058865)。

**既知の問題**  
なし

**修正**
1. メンテナンス プランの名前と最初の SUB_PLAN 名が同じである場合、メンテナンス プランの移動のタスク中に SSMS がクラッシュします。
2. SQL Server Management Studio (SSMS) で sp_executesql を呼び出すストアド プロシージャをデバッグすることはできません。 F11 キーを押すと、'オブジェクト参照がオブジェクト インスタンスに設定されていません' というエラー メッセージが表示されます ([Microsoft Connect アイテム #736509](https://connect.microsoft.com/SQLServer/feedback/details/736509/sql-server-2012-rtm-management-studio-cannot-debug-sp-executesql))。
3. SSMS が SQL Server Express でフルテキストを完全に管理しません ([Microsoft Connect アイテム #740181](https://connect.microsoft.com/SQLServer/feedback/details/740181/management-studio-does-not-fully-manage-full-text-in-sql-server-express))。
4. SSMS が、番号付きストアド プロシージャを一貫性なく処理します [(Microsoft Connect アイテム #764197](https://connect.microsoft.com/SQLServer/feedback/details/764197/ssms-2012-inconsistently-handles-numbered-procedures))。
5. SSMS が終了時にクラッシュし、自動的に再起動する場合があります ([Microsoft Connect アイテム #774317](https://connect.microsoft.com/SQLServer/feedback/details/774317/sql-server-management-studio-2012-2014-crashes-when-closing))。
6. SSMS で列レベルの権限をスクリプト化すると、スクリプトの作成でステートメントが重複します ([Microsoft Connect アイテム #797967](https://connect.microsoft.com/SQLServer/feedback/details/797967/ssms-create-script-duplicates-the-statements-for-grant-or-deny-column-permissions))。
7. タスク バーで SSMS のウィンドウ アイコンを更新しようとすると、SSMS がクラッシュする場合があります ([Microsoft Connect アイテム #799430](https://connect.microsoft.com/SQLServer/feedback/details/799430/ssms-2012-sp-1-cu-5-installed-crash-when-enforce-refresh-on-connect))。

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2012-sp3httpdownloadmicrosoftcomdownloadf67f673709c-d371-4a64-8bf9-c1dd73f60990enux86sqlmanagementstudiox86enuexe"></a>![ダウンロード](../ssdt/media/download.png) [SQL Server Management Studio 2012 SP3](http://download.microsoft.com/download/F/6/7/F673709C-D371-4A64-8BF9-C1DD73F60990/ENU/x86/SQLManagementStudio_x86_ENU.exe)  
  
2015 年 11 月 21 日 | バージョン番号: 11.0.6020.0

**機能**  
豊富な機能を備える SSMS Express エディション。 コード スニペット。 列ストア インデックスなど。  
[詳細については、リリース ノートをご覧ください。](https://support.microsoft.com/en-us/kb/3072779)
 
**既知の問題**  
なし

**修正**
1. インポートおよびエクスポート ウィザードを使用してデータをインポートすると、見つからない列がエラー メッセージで示されません。
2. SSMS での差分バックアップを復元すると、「復元プランを作成できません。LSN チェーンが破損しています」というエラーが表示されます。

---
## <a name="additional-downloads"></a>追加のダウンロード  
すべての SQL Server Management Studio ダウンロードの一覧については、「[Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending)」を検索してください。  
  
SQL Server Management Studio の最新リリースについては、「[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)」をご覧ください。  

---  
## <a name="related-resources"></a>関連リソース
[Update center for Microsoft SQL Server (Microsoft SQL Server の更新センター) (Microsoft SQL Server の更新センター)](https://technet.microsoft.com/sqlserver/ff803383.aspx)   
[SQL Server Management Studio クイック スタートに関するページ](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[SQL Server Management Studio フォーラムに関するページ](https://social.msdn.microsoft.com/forums/en-us/home?forum=sqltools)  

  

