---
title: SQL Server の機械学習と R サービスで R スクリプトのエラー |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0b695111849b234f6ca38fc89c538e905f187fb6
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34709103"
---
# <a name="r-scripting-errors-in-sql-server"></a>SQL Server で R スクリプトのエラー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、SQL Server で R コードを実行する場合に、いくつかの scriptin gerrors を説明します。 一覧ではありません。 多くのパッケージがあるし、エラーは、同じパッケージのバージョンによって異なります。 スクリプト エラーの送信をお勧め、 [Machine Learning Server フォーラム](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR)をサポートする、機械学習 R Services (In-database)、Microsoft R クライアント、および Microsoft R Server で使用されるコンポーネントです。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>T-SQL で、ストアド プロシージャでは有効なスクリプト失敗

ストアド プロシージャで R コードをラップする前に、外部の IDE でまたは RTerm RGui などの R ツールのいずれかの R コードを実行することをお勧めします。 これらのメソッドを使用するには、テストおよび R. によって返される詳細なエラー メッセージを使用してコードをデバッグすることができます。

ただし、場合があります、外部の IDE またはユーティリティで完全に動作するコードが失敗するストアド プロシージャの実行または SQL Server のコンピューティング コンテキストにします。 このような場合は、さまざまなパッケージを SQL Server で動作しないことを想定する前に検索する問題があります。

1. スタート パッドが実行されているかどうかを確認します。

2. メッセージ入力データまたは出力データに互換性がないか、サポートされていないデータ型の列が含まれているかどうかを確認します。 たとえば、SQL データベースでクエリは、Guid または RowGUIDs、どちらもサポートされていないを多くの場合、返されます。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

3. SQL Server のコンピューティング コンテキストのすべてのパラメーターがサポートされているかどうかを決定する個々 の R 関数のヘルプ ページを確認します。 ScaleR ヘルプ コマンドを使用して、インライン R ヘルプ、または参照してください[パッケージ参照](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)です。

R ランタイムが機能している、スクリプトがエラーを返す場合は、R Tools for Visual Studio など、専用の R 開発環境でスクリプトをデバッグしようとすることをお勧めします。

お勧め確認し、R とデータベース エンジンの間でデータを移動するときに発生する可能性がありますのあるデータ型に関する問題を修正するスクリプトを少し修正することです。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

さらに、ストアド プロシージャとしてより簡単に使用した形式で、R スクリプトをバンドルするのに sqlrutils パッケージを使用することができます。 詳細については、以下をご覧ください。
* [Sqlrutils パッケージを使用して R コードをストアド プロシージャを生成します。](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Sqlrutils を使用してストアド プロシージャを作成します。](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>スクリプトが矛盾する結果を返します

R スクリプトは、いくつかの理由、SQL Server のコンテキストで別の値を返すことができます。

- 暗黙の型変換は、データが SQL Server と R. の間で渡されるときに、自動的に一部のデータ型の実行します。詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

- ビット数が倍であるかどうかを確認します。 たとえば、32 ビットおよび 64 ビットの浮動小数点ポイント ライブラリの算術演算の結果の違いは少なくありません。

- NaNs が任意の操作で生成されたかどうかを決定します。 結果がこれを無効にできます。

- ゼロに近い数値の逆数を取得すると、若干の違いが増幅されることができます。

- 蓄積されたエラーの丸めなどの値がゼロではなく 0 未満にする可能性があります。

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>ODBC 経由でリモート実行の暗黙の認証

接続する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] R を実行するコンピューターのコマンドを使用して、 **RevoScaleR**関数、サーバーにデータを書き込む ODBC 呼び出しを使用するとエラーを発生可能性があります。 このエラーは、Windows 認証を使用している場合にのみ発生します。

R Services に対して作成されるワーカー アカウントに、サーバーに接続する権限がないことです。 したがって、あなたの代理として ODBC 呼び出しを実行できません。 問題は、ため、SQL ログインを持つ資格情報は、明示的にクライアントから渡される、R し、次の SQL Server インスタンスに ODBC に SQL ログインを持つ生じません。 ただし、SQL ログインを使用しても安全性は低く Windows 認証を使用するよりもします。

リモートでの SQL Server が開始したスクリプトから安全に渡される Windows 資格情報を有効にするには、資格情報をエミュレートする必要があります。 このプロセスと呼ばれる_黙示的な認証_です。 この作業をするためには、SQL Server コンピューターの R または Python スクリプトを実行しているワーカー アカウントが適切なアクセス許可が必要です。

1. 開いている[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]R コードを実行するインスタンスの管理者として。

2. 次のスクリプトを実行します。 ユーザー グループの場合、名前、既定値を変更して、コンピューター名とインスタンス名を編集することを確認します。

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>SQL のコンピューティング コンテキストで R を実行しているときに、ワークスペースをオフにしないで

R コンソールで作業するときは、一般的なは、ワークスペースをオフにして、そのことが予期しない結果に、SQL の計算コンテキスト。

`revoScriptConnection` SQL Server から呼び出される R セッションに関する情報を含む R ワークスペースにオブジェクト。 ただしかどうか、R コードは ワークスペースをオフにするコマンド (など`rm(list=ls())`)、セッションとの R ワークスペースには、他のオブジェクトに関するすべての情報はもオフにします。

この問題を回避するには、SQL Server で R を実行しているときに、変数およびその他のオブジェクトの区別しないで消去しないでください。 使用して特定の変数を削除することができます、**削除**関数。

```R
remove('name1', 'name2', ...)
```

複数の変数を削除する場合は、一時変数の名前を一覧に保存し、一覧に定期的なガベージ コレクションを実行お勧めします。



## <a name="next-steps"></a>次のステップ

[Machine Learning のサービスのトラブルシューティングと既知の問題](machine-learning-troubleshooting-faq.md)

[機械学習のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

[アップグレードとインストールに関してよく寄せられる質問](r/upgrade-and-installation-faq-sql-server-r-services.md)

[データベース エンジンの接続をトラブルシューティングします。](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
