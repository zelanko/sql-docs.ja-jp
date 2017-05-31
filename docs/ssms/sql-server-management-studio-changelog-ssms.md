---
title: SQL Server Management Studio - Changelog (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2144751277bb10897e0ed39ee24dbad8a32b4ce
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

## <a name="ssms-1653-release"></a>SSMS 16.5.3 リリース
一般公開 | ビルド番号: 13.0.16106.4

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


## <a name="ssms-1651-release"></a>SSMS 16.5.1 リリース
一般公開 | ビルド番号: 13.0.16100.1

* 制約の確認時に Invoke-Sqlcmd で誤って複数の行が挿入されるという問題を修正しました。 [Microsoft Connect アイテム: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* 可用性グループの作成時に ENU 以外の言語バージョンが完全に動作しないという問題を修正しました。

* クエリ プラン XML をクリックしたときに適切な SSMS UI が開かないという問題を修正しました。


## <a name="ssms-165-release"></a>SSMS 16.5 リリース
一般公開 | ビルド番号: 13.0.16000.28

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


## <a name="ssms-1641-september-2016-release"></a>SSMS 16.4.1 (2016 年 9 月) リリース
一般公開 | ビルド番号: 13.0.15900.1

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



## <a name="ssms-163-august-2016-release"></a>SSMS 16.3 (2016 年 8 月) のリリース
一般公開 |バージョン番号: 13.0.15700.28

* SSMS の毎月のリリースは番号が付けられるようになりました。

* [新しい認証オプション **「Active Directory ユニバーサル認証」**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)。 これは、多要素、パスワード、および統合認証メカニズムをサポートする Azure Active Directory によって実行されるトークン ベースの認証メカニズムです。

* SQL Server Profiler テンプレートの機能に適した新しい拡張イベント テンプレート [(Microsoft Connect アイテム #2543925)](https://connect.microsoft.com/SQLServer/feedback/details/2543925/sql-server-extended-events-profiler-tool)。 同梱の [SQL Server Profiler テンプレート](https://msdn.microsoft.com/library/ms190176.aspx)の詳細を表示します。

* Azure SQL データベースの新しい [データベースの作成] と [データベースのプロパティ] ダイアログ ボックス。

* PowerShell を使用して SQL Server ログインの管理を実行するための新しい ’Get SqlLogin’ コマンドレットと 'Remove-SqlLogin’ コマンドレット。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2588952。](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* 任意のプロバイダーとキー パスの列マスター キーの作成のサポートを追加する新しい PowerShell コマンドレット ’New-SqlColumnMasterKeySettings’。

* SSMS での Azure SQL データベースの作成を効率化する新しい [データベースの作成] ダイアログ ボックス。

* SSMS オブジェクト エクスプ ローラーの 'データベース' のノードでのフィルタリングのサポート。 データベースの一覧をフィルター処理するには、オブジェクト エクスプ ローラーで 'データベース' ノードに移動し、オブジェクト エクスプ ローラーのツールバーでフィルター アイコンをクリックします。

* [バックアップと復元] ウィザードでの Azure Resource Manager (ARM) タイプのストレージ アカウントのサポート。

* [高解像度表示の初期ベータ版のサポート](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display)、 [Microsoft Connect アイテム #1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/)、 [Microsoft Connect アイテム #1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/)、 [Microsoft Connect アイテム #1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/)、  [Microsoft Connect アイテム #1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/)、 [Microsoft Connect アイテム #2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/)、 [Microsoft Connect アイテム #1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/)、 [Microsoft Connect アイテム #1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/)、 [Microsoft Connect アイテム #2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/)、 [Microsoft Connect アイテム #1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/)、 [Microsoft Connect アイテム #2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/)、 [Microsoft Connect アイテム #2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/)、 [Microsoft Connect アイテム #2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/)、 [Microsoft Connect アイテム #2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/)、 [Microsoft Connect アイテム #1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/)、 [Microsoft Connect アイテム #2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/)、 [Microsoft Connect アイテム #2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/)、 [Microsoft Connect アイテム #2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* SQL Server クエリ ストアからのワークロードの自動読み取りをサポートするためのデータベース エンジン チューニング アドバイザー (DTA) を機能強化。

* クラスター化列ストア インデックス、非クラスター化列ストア インデックス、および行ストア インデックスに関するインデックスの推奨事項を表示するよう、データベース エンジン チューニング アドバイザー (DTA) を機能強化。

* SQL Server Analysis Services PowerShell コマンドレットを使用したデータベース コンソール (DBCC) コマンドの送信のサポート。

* SSMS で、復号化された AlwaysEncrypted ラージ オブジェクト (LOB) 列のクリア テキストを表示するようバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Windows の視覚スタイルが有効でない場合のクラッシュを解決するよう [Always Encrypted] ダイアログボックスのバグを修正。

* SQL Server インスタンスへの接続を妨げる 'メソッドが見つかりませんでした' エラーのバグを修正。

* datetimeoffset を含むパーティション関数を作成するときの SSMS クラッシュのバグを修正。

* Distributed Replay 管理ツール (DReplay.exe) を起動するための Microsoft .NET 3.5 の削除要件を追加するようバグを修正。

* サーバーの完全修飾名をサポートするよう [Analysis Services 配置] ウィザードのバグを修正。

* 2016 互換性モデルの Analysis Services 表形式モデルでパーティションを表示するよう SSMS のバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Analysis Services 表形式モデルおよび SQL Server 共有管理オブジェクト (SMO) におけるパフォーマンスの改善およびバグの修正。 


---
## <a name="ssms-july-2016-hotfix-update-release"></a>SSMS 2016 年 7 月修正プログラムのリリース 
一般公開 |バージョン番号: 13.0.15600.2

* **不足している右クリック メニュー項目を有効にするよう SSMS のバグを修正**。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Microsoft Connect アイテム #2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Microsoft Connect アイテム #2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016-release"></a>SSMS 2016 年 7 月のリリース 
一般公開 |バージョン番号: 13.0.15500.91

* *7 月 5 日編集:* **Analysis Services プロセス ダイアログと Analysis Services の配置ウィザードの、表形式データベース向けの SQL Server 2016 (互換性レベル 1200) のサポートを強化。**

* *7 月 5 日編集:* **'XACT_ABORT' を設定する SSMS の [クエリ実行オプション] ダイアログ ボックスの新しいオプション。このオプションは、このSSMSリリースでは既定で有効になっています。実行時エラーが発生した場合に、SQL Server にトランザクション全体をロールバックし、バッチを中止する指示をします。**

* **SSMS での Azure SQL Data Warehouse のサポート。**

* **SQL Server PowerShell モジュールの大幅な更新。これには、新しい [SQL PowerShell モジュールと、Always Encrypted の新しいコマンドレット、SQL エージェント、SQL エラー ログ](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)**が含まれます。

* **Always Encrypted ウィザードでの PowerShell スクリプトの生成のサポート**。

* **Azure SQL データベースへの接続時間を大幅に短縮。**

* **新しい 'Backup to URL' ダイアログによって、SQL Server 2016 データベースのバックアップ向けの Azure Storage の資格情報の作成をサポート。これにより、データベースのバックアップを Azure Storage アカウントにより効率的に格納できます。**
 
* **新しい復元ダイアログによって、Microsoft Azure Storage サービスからの SQL Server 2016 データベース バックアップの復元を効率化。**
 
* **ユーザーが SELECT 権限を持っていない場合に、SSMS クエリ デザイナーにテーブルを追加できるようバグを修正。**

* **'TRY_CAST()' と 'TRY_CONVERT()' 関数の IntelliSense サポートを追加するためのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast)。

* **'SQLAS' Analysis Services 拡張機能の読み込みを有効にするための PowerShell モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension)。

* **ドラッグ アンド ドロップで Sql ファイルを開くことができるよう、SSMS のエディター ウィンドウのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios)。

* **終了時のプロファイラーのクラッシュを修正するようプロファイラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped)。  
[Microsoft Connect アイテム #2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968)。

* **SSMS テーブル デザイナーでの結合のリンクを編集しようとする際のクラッシュを防ぐよう、SSMS のバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms)。

* **Db_owner ロールのメンバーのデータベース スクリプトの生成を有効にするよう SSMS のバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june)。

* **サーバーがオフラインになった場合、[クエリ] タブを閉じるときの遅延を回避するよう SSMS エディターのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline)。

* **SQL Server Express データベースのバックアップ オプションを有効にするようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks)。  
[Microsoft Connect アイテム #2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance)。

* **多次元の Analysis Services モデルのデータ フィード プロバイダーが正しく示されるよう、Analysis Services のバグを修正。**

----
## <a name="ssms-june-2016-generally-available-release"></a>SSMS 2016 年 6 月の一般公開リリース
一般公開 |バージョン番号: 13.0.15000.23

* **SSMS を 2016 年 6 月リリースから一般公開。**

* **現在のドキュメントへの統合が強化され、正規表現を使用した検索が可能な SSMS の新しいクイック検索ダイアログ。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* **スクリプトを使用した無人インストールのインストール進行状況とプロセス終了コードを追跡できるよう、SSMS インストーラーを機能強化。**

* **ヘルプ ドキュメントおよび記事を正しく表示できるよう、SSMS の状況依存の F1 ヘルプのバグを修正。**

* **スクロール時に SSMS のクラッシュの原因となるクエリ データ ストア '低下したクエリ' ビューのバグを修正。** 

* **Excel 2016 から SQL Server Analysis Services への接続を許可するよう、Excel Analysis Services OLEDB コネクタのバグを修正。**

* **マルチ モニター システムで、SSMS のメイン ウィンドウと同じのモニターに [接続] ダイアログ ボックスを表示するよう、SSMS の [接続] ダイアログ ボックスのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* **Always Encrypted エクスペリエンスのバグを修正。Always Encrypted メニュー オプションが Stretch Database に対して正しく有効にならないバグを修正しました。また、SafeNet (Luna SA) HSM プロバイダーを正しく使用しない Always Encrypted ウィザードのバグも修正しました。**

---
## <a name="ssms-april-2016-preview"></a>SSMS 2016 年 4 月プレビュー 
バージョン番号: 13.0.14000.36
  
* **人間が判読できるエラー メッセージを追加するための SSMS インストーラーの機能強化。**  
  
* **述語のサポートを追加するための Stretch Database ウィザードの機能強化**。  
  
* **キーの暗号化 API を追加するための AlwaysEncrypted Powershell コマンドレットの機能強化**。  
  
* **[ツール オプション] ダイアログ ボックスで IntelliSense を無効にしている場合、SSMS ツールバーで IntelliSense をオフにするようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2555163/sql-2016-rc2-turning-off-intellisense-from-options-does-not-turn-it-off-on-toolbar/>  
    
* **時間のかかるクエリ プランで使用される間隔を減らすための、プラン表示の比較ユーザーインターフェイスの機能強化およびバグの修正**。  
  
* **SSMS を終了するとクラッシュの原因となった問題を修正するよう、SSMS のバグを修正**。   
  
* **暗号化中にユーザーのアクセス許可を保持し、ウィザードの完了後にデータベースによる操作のデタッチを許可するよう、Always Encrypted ウィザードのバグを修正**。  
  
* **サポートされていない暗号化アルゴリズム (CNG) プロバイダーを使用してキーを生成しようとしたときにフィールドバックを送信するための、Always Encrypted の [新しい列マスター キー] ダイアログ ボックスのバグを修正。**  
  
---  
## <a name="ssms-march-2016-preview-refresh"></a>SSMS 2016 年 3 月プレビューの更新
バージョン番号: 13.0.13000.55
  
* **SSMS では、Visual Studio 2015 の分離シェルを使用するようになりました。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2390544/update-ssms-to-use-visual-studio-2015-dependencies/>  
  
* **メニュー項目やオプションをすばやく見つけるのをサポートする新しいクイック起動ツールバー。(VS 2015 分離シェル)**  
  
* **SSMS ライト テーマのサポートを追加するための SSMS テーマ オプションの機能強化。(VS 2015 分離シェル)**  
  
* **[既定値にリセット] ボタンが押された場合にクエリのショートカットが正しくリセットされるよう、SSMS メニュー オプションを修正。**  
  
* **簡単に読み取り可能なテンプレートの名前を表示するよう、SSMS の新しいプロジェクト テンプレートのバグを修正。**  
  
* **SSMS で SQL エージェント ジョブ履歴を表示する際のエラーを解決。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2458860/error-viewing-job-history-microsoft-datawarehouse-sqm/>  
    
* **SSMS のオフライン インストールができるようバグを修正。これにより、インターネット接続がなくてもインストールできます。(VS 2015 分離シェル)**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2497178/cannot-install-ssms-when-server-has-no-internet-access/>  
    
* **SQL Server PowerShell (SQLPS) モジュールをインポートしたときにユーザーの現在のディレクトリが保持されるようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2434605/loading-sqlps-module-changes-current-directory-to-ps-sqlserver/>  
    
* **承認済みの PowerShell 動詞を使用するよう SQL Server PowerShell (SQLPS) モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2432891/sqlps-module-uses-unapproved-powershell-verbs/>  
    
* **モジュールを高速に読み込むよう、SQL Server PowerShell (SQLPS) モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2429153/sqlps-module-is-slow-to-load/>  
    
* **ジョブ ステップの変更を許可するよう、SQL エージェント ジョブ ステップのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2453996/issues-with-agent-in-ssms-2016-rc0-13-0-12000-65/>  
    
* **アルファベット順にテーブルを一覧表示するよう、SSMS オブジェクト エクスプ ローラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2424718/sql-server-2016-ssms-table-list-confusing/>  
    
* **SQL Server の接続が変更されたときにデータベース名の正確な一覧が表示されるよう、[使用できるデータベース] ドロップダウン リストのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2513420/available-databases-drop-down-box-does-not-update-when-connection-changes-in-ssms/>  
    
* **'CTRL + U' のキーボード操作が行われたときに [使用できるデータベース] ドロップダウン リストにフォーカスを移動するよう、SSMS のキーボード ショートカットのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2534820/ssms-ctrl-u-doesnt-work/>  
  
---  
## <a name="ssms-march-2016-preview"></a>SSMS 2016 年 3 月プレビュー 
バージョン番号: 13.0.12500.29 
  
* **キーボードのキーを使用したナビゲーションを許可するための SSMS Web インストーラーの機能強化。**  
  
* **暗号化の別名データ型をサポートするための AlwaysEncrypted ウィザードの機能強化。**  
  
* **正しい数の最大の自動フェールオーバー ターゲットを表示するよう、AlwaysOn '新しい可用性グループ' ウィザードのバグを修正。**  
*リンクされている、顧客のバグ要求:* <https://connect.microsoft.com/SQLServer/feedback/details/2333670/ssms-is-showing-the-wrong-number-of-maximum-automatic-failover-targets/>  
    
* **インストールに影響するエラーを修正するために SSMS Web インストーラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2181548/sql-server-2016-ctp-3-2-management-studio-setup/>  
    
* **SQL Server 2012 以下のメンテナンスを保存できるよう、SSMS プレビュー リリースのバグを修正。**  
      
* **ストライプ バックアップに対して複数のカスタムバックアップ名を許可して、ストレージの資格情報を選択した後に新しい名前を入力した場合に適切なバックアップ ファイルの名前を表示するよう、バックアップ ウィザードのバグを修正。**  
  
---  
## <a name="ssms-february-2016-preview"></a>SSMS 2016 年 2 月プレビュー 
バージョン番号: 13.0.12000.65
  
* **SSMS でハイ コントラスト設定が有効になっているときに、テキストのオプションを表示するための利用状況モニターの機能強化。**  
  
* **列の照合順序が暗号化プロセス中に変更された場合に警告を表示するための Always Encrypted ウィザード ダイアログ ボックスの機能強化。**  
  
* **列暗号化キー、列暗号化キーの値、および列のマスター キーで条件を作成するためのサポートを追加するポリシー管理の機能強化。**  
  
* **Always Encrypted マスター キーのクリーンアップのダイアログの使いやすさおよび Always Encrypted エラー メッセージを改善するようバグを修正。**  
  
* **キーが 1 つしか存在しない場合に Always Encrypted 列マスター キーの交換を無効にするようバグを修正。**  
  
* **SSMS 1 月リリース、または SQL Server RC0 メディアにバンドルされている SSMS リリースを使用して Always Encrypted を起動した場合に発生する '型の初期化子' エラーのバグを修正。**  
  
---  
## <a name="ssms-january-2016-preview"></a>SSMS 2016 年 1 月プレビュー 
バージョン番号: 13.0.11000.78 
  
* **拡張イベント (XEvent) セッションを削除できるようにするための SSMS でのバグ修正。**  
  
* **SQL Server 2014 可用性グループのプロパティ ダイアログを開くためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/1609719/>  
     
* **Azure のレプリカを可用性グループに追加する機能を有効にするためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2029135/>  
     
* **SQL Server 2014 データベースのプロパティ ダイアログを開くためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2080209/>  
     
* **Azure SQL Database への接続時に各テーブルに表示される重複した列を削除するためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2103116/>  
---  
## <a name="ssms-december-2015-preview"></a>SSMS 2015 年 12 月プレビュー 
バージョン番号: 13.0.900.73
  
* **現在のクエリ実行プランとファイルに保存されたプランとの比較を可能にする Showplan 比較の機能強化。**  
  
* **SSMS でのインライン列ストア インデックスの IntelliSense サポート強化。**  
  
* **Azure V12 サーバーに接続しているときにテンプレートの選択を有効にする拡張イベント セッション ウィザードのバグ修正。**  
  
* **[セキュリティ] フォルダーの [監査の作成] と [新しいログイン] ダイアログのタブ位置が新しくなり、キーボードの操作性が向上。**  
  
* **グリッド形式で結果を表示するように SSMS を設定した場合に、"クエリ実行後に [結果] タブに切り替える" 機能を有効にするためのバグ修正。**   
 *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1390296/switch-to-results-tab-after-query-execution-grid-mode-in-ssms-2016>  
  
* **SSMS をグリッド形式で結果を表示するように設定した場合に、切り詰められていない列ヘッダーを表示するためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/2004111/bugbash-column-headers-in-grid-mode-truncated-with-courier-new-8>  
      
* **バグ修正により、SSMS Web インストーラーの適切なインストールが可能。**  
 *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2003865/ssms-october-preview-incoherent-error-message>  
<https://connect.microsoft.com/SQLServer/feedback/details/2079557/unable-to-instal-sql-server-update-13-0-800-111-over-13-0-700-242-error-code-2711>  
  
---  
## <a name="ssms-november-2015-preview"></a>SSMS 2015 年 11 月プレビュー
バージョン番号: 13.0.800.111
  
* **SSMS の高解像度用ディスプレイ ビットマップ スケーリングをサポート。**  
  
* **AlwaysEncrypted ダイアログとウィザードのユーザー インターフェイスを改善し、データベース暗号化キーの作成プロセスを簡略化。**  
  
* **[Activity] モニターの [プロセス] 一覧に追加された新しい右クリック コンテキスト メニュー オプションで Live Query 統計情報を表示。**  
  
* **バグ修正により、クライアント コンピューターで SSMS プレビュー リリースの適切なアンインストールが可能。**  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1868474/ssms-2016-preview-can-be-installed-but-not-uninstalled>  
  
* **ファイルがなくても SQL ジョブ エージェントのジョブ ステップの編集を許可するためのバグ修正**。  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
    <https://connect.microsoft.com/SQLServer/feedback/details/1502100/ssms-preview-error>  
      
* **Azure の仮想マシンで実行しているデータベースの拡張イベント セッションの [ターゲット データの表示] メニュー オプションのバグ修正。**  
  *リンクされている、顧客のバグ要求*:  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
***  

## <a name="ssms-october-2015-preview"></a>SSMS 2015 年 10 月プレビュー 
バージョン番号: 13.0.700.242  
* **新しく革新的で軽量な Web インストーラー。SSMS のダウンロードとインストールのプロセスを簡略化します。**  
  
* **新しい Always Encrypted 列暗号化ウィザード。クライアント側での選択した列の暗号化と復号化が可能です。**  
  
* **新しい列マスター キー (CMK) 回転ダイアログ。Always Encrypted データベース用で、データを保護するための暗号化キーの回転プロセスを簡略化します。**  
  
* **新しいストレッチ データベース モニター。Azure クラウドへのデータ移行の状態のトラブルシューティングと監視を行うことができます。**  
  
* **Stretch Database ウィザードの機能強化。既定では Microsoft Azure サブスクリプションに含まれない Microsoft Azure サーバーの選択をサポートしています。**  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1687063/cannot-choose-from-multiple-microsoft-azure-subscriptions>  
* **SSMS でライブ実行プランを適切に表示できるようにするためのバグ修正。**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1774446/viewing-live-execution-plan-from-activity-monitor-crashes-ssms>    
* **データベース スナップショットの SSMS スクリプトにおける無効なオプションを削除するためのバグ修正**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1515168/ssms-scripting-of-database-snapshots-includes-invalid-options>  
* **[トップ リソースのコンシューマー クエリ] ウィンドウで詳細を表示するためのクエリ データ ストア UI のバグ修正。**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1737185/sql-server-2016-overall-resource-consumption-query-store-pane-issue>  
***  

## <a name="ssms-september-2015-preview"></a>SSMS 2015 年 9 月プレビュー 
バージョン番号: 13.0.600.65  
* **Azure SQL Database への接続プロセスを効率化する、新しいファイアウォール ルール ダイアログ。**      
    
* **[新しいインデックス] ダイアログの更新。クラスター化列ストア インデックスが存在する場合でもクラスター化されていない行ストア インデックスを作成できます。この機能は、SQL 2016 以降で利用できます。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1552617/creation-of-nc-index-when-clustered-columnstore-index>  
      
* **Windows 7 で実行される SSMS プレビュー版リリースの SQL エージェント ジョブ ステップを表示と編集できるようにするためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1548140/cannot-view-or-edit-any-sql-agent-job-step>    
  <https://connect.microsoft.com/SQLServer/feedback/details/1626895/unable-to-load-dll-dts>    
  <https://connect.microsoft.com/SQLServer/feedback/details/1576662/error-creating-new-job-step>     
      
* **SQL Server 2014 以降の SSMS におけるトリガー ノードを表示するためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1617533/trigger-node-missing>   
      
* **ヘッダーからバージョン情報を除外するための、データベースとサーバーの標準レポート ユーザー インターフェイスにおけるバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1387471/report-headings-wrongly-named>  
      
* **ライブ クエリ統計ノードで、完了していないにもかかわらず完了と表示されないようにするためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1589096/live-query-statistics-node-shows-as-completed>  
  
***      
## <a name="ssms-august-2015-preview"></a>SSMS 2015 年 8 月プレビュー 
バージョン番号: 13.0.500.53
  
* **オブジェクト エクスプローラーの更新。データベースが多数存在する場合の読み込み遅延を減らします。**  
  
* **Windows 10 コンピューターでの SSMS インストールの機能強化。**  
  
* **SQL Server 構成マネージャーと SSMS ユーザー レポートのユーザー インターフェイスのバグ修正と更新。**    
***  
  
## <a name="ssms-july-2015-preview"></a>SSMS 2015 年 7 月プレビュー
バージョン番号: 13.0.400.91
  
* **Azure SQL Database (V12) のデータベース ダイアグラム。**  
  
* **新しいテンポラル テーブル構文に関する IntelliSense サポートの強化。**  
  
* **DacFx library ライブラリの更新。行レベルのセキュリティと Azure Active directory 認証を含む最新の Azure SQL Database 機能をサポートします。**  
  
* **バグ修正 ([更新プログラムの確認] UI の更新、[互換性レベル] 一覧などにおける UI 修正)。**  
***  
  
## <a name="ssms-june-2015-preview"></a>SSMS 2015 年 6 月プレビュー 
バージョン番号: 13.0.300.44
  
* **SSMS の新しい軽量 Web インストーラー。**  
  
* **自動的な更新プログラムの確認。**  
  
* **SSMS で、Azure SQL Database (V12) のフル テキスト検索をサポートするようになりました。**  
  
* **お客様から要求が最も多い次の問題に対応しました。**  
  * オブジェクト エクスプローラーのテーブルとビューに関して [上位 200 行を編集] を利用できるようになりました。  
  * Azure SQL Database (V12) に関してテーブル デザイナーを使用できます。  
  * Azure SQL Database (V12) で、データベースとテーブルのプロパティのダイアログを使用できるようなりました。  
    
 * **T-SQL ファイルを保存するように求めるメッセージをスキップする新しいオプション。**  
   
 * **新しい Azure SQL Database サービス レベル (Basic、Standard、Premium) での Import/Export ウィザードのサポート。**  
   
 * **多くのバグ修正 (スクリプト作成シナリオ、SQL データベースの変更追跡の有効化など)。**   
     
  
  
  
  
  
  
    

