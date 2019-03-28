---
title: R スクリプトのエラーとトラブルシューティング - SQL Server Machine Learning サービス
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2df4fa2fd9ef52fe5edbca9440f73f351553f1ed
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511529"
---
# <a name="r-scripting-errors-in-sql-server"></a>SQL Server で R スクリプトのエラー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R コードを実行するときに、いくつかの scriptin gerrors を説明します。 一覧では、大文字と小文字は包括的なありません。 多くのパッケージがあるし、エラーは、同じパッケージのバージョンによって異なります。 スクリプトのエラーの送信をお勧め、 [Machine Learning Server フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR)、machine learning R Services (In-database)、Microsoft R Client、および Microsoft R Server で使用されるコンポーネントをサポートしています。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>有効なスクリプトは、T-SQL またはストアド プロシージャが失敗しました。

ストアド プロシージャで R コードをラップする前はまたは RTerm、RGui などの R ツールのいずれかで外部の IDE で R コードを実行することをお勧めします。 これらのメソッドを使用するには、テストおよび R. によって返される詳細なエラー メッセージを使用して、コードをデバッグすることができます。

ただし、場合があります、外部の IDE またはユーティリティで完全に動作するコードはストアド プロシージャで実行したり、SQL server 計算コンテキストを失敗可能性があります。 この場合は、さまざまな問題を探して前に、パッケージを SQL Server で動作しないことを想定しています。

1. スタート パッドが実行されているかどうかを確認します。

2. メッセージは、入力データと出力データに互換性がないかサポートされていないデータ型の列が含まれているかどうかを確認します。 たとえば、SQL database でのクエリは Guid または RowGUIDs、どちらもサポートされていないを返す多くの場合。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)します。

3. SQL Server のコンピューティング コンテキストのすべてのパラメーターがサポートされているかどうかを判断する個々 の R 関数のヘルプ ページを確認します。 ScaleR のヘルプについては、R のインライン ヘルプのコマンドを使用して、または参照してください[パッケージ参照](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)します。

R ランタイムが機能している、スクリプトがエラーを返す場合は、R Tools for Visual Studio など、専用の R 開発環境でスクリプトのデバッグを試してみることをお勧めします。

私たちはまた、確認し、R とデータベース エンジンの間でデータを移動するときに生じる可能性のあるデータ型に関する問題を修正するスクリプトを少し修正することお勧めします。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)します。

さらに、ストアド プロシージャとしてより簡単に使用される形式で R スクリプトをバンドルするのに sqlrutils パッケージを使用することができます。 詳細については、以下をご覧ください。
* [sqlrutils パッケージ](r/ref-r-sqlrutils.md)
* [Sqlrutils を使用してストアド プロシージャを作成します。](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>スクリプトには、一貫性のない結果が返されます。

R スクリプトは、いくつかの理由、SQL Server のコンテキストで異なる値を返すことができます。

- 暗黙的な型変換は SQL Server と R. 間のデータが渡されるときに、自動的に一部のデータ型の実行します。詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)します。

- ビットが要因であるかどうかを確認します。 たとえば、32 ビットおよび 64 ビットの浮動小数点ポイント ライブラリの算術演算の結果の違いは多くの場合。

- Nan は、いずれかの操作で生成されたかどうかを決定します。 結果がこれを無効にできます。

- ゼロに近い数の逆数を取得すると、小さな違いを増幅されることができます。

- 丸めの誤差が累積などの値がゼロではなく 0 未満にする可能性があります。

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>ODBC 経由のリモート実行の暗黙の認証

接続する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] R を実行するコンピューターのコマンドを使用して、 **RevoScaleR**関数の場合、サーバーにデータを書き込む ODBC 呼び出しを使用するときにエラーを発生可能性があります。 このエラーは、Windows 認証を使用している場合にのみ発生します。

理由は、R Services に対して作成されるワーカー アカウントに、サーバーに接続する権限がないことです。 そのため、ODBC 呼び出しを自動的に実行できません。 問題はため、SQL ログイン名、資格情報明示的に渡される、R クライアントから SQL Server インスタンスに ODBC にし、SQL ログインでは発生しません。 ただし、SQL ログインを使用して、Windows 認証を使用してほど安全でも。

リモートでの SQL Server が開始したスクリプトから安全に渡される Windows 資格情報を有効にするには、資格情報をエミュレートする必要があります。 このプロセスと呼ばれる_暗黙の認証_します。 この作業をするためには、SQL Server コンピューターで R または Python スクリプトを実行するワーカー アカウントは、適切なアクセス許可が必要です。

1. 開いている[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]R コードを実行するインスタンスの管理者として。

2. 次のスクリプトを実行します。 既定値を変更した場合、ユーザー グループ名とコンピューターとインスタンス名を編集してください。

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>SQL 計算コンテキストで R を実行しているときに、ワークスペースをクリアできません。

ワークスペースをクリアすると、R コンソールで作業するときに一般的なは、予期しない結果に SQL 計算コンテキスト。

`revoScriptConnection` SQL Server から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードがワークスペースをクリアするためのコマンドを含むかどうか (など`rm(list=ls())`)、セッションと R ワークスペース内の他のオブジェクトに関するすべての情報がもクリアされます。

この問題を回避するには、SQL Server で R を実行しているときに、変数とその他のオブジェクトを無差別にクリアしないようにします。 使用して特定の変数を削除することができます、**削除**関数。

```R
remove('name1', 'name2', ...)
```

複数の変数を削除する場合は、一時変数の名前を一覧に保存し、リストの定期的なガベージ コレクションを実行することが推奨されます。



## <a name="next-steps"></a>次のステップ

[Machine Learning サービスのトラブルシューティングと既知の問題](machine-learning-troubleshooting-faq.md)

[Machine learning のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

[アップグレードとインストールに関してよく寄せられる質問](r/upgrade-and-installation-faq-sql-server-r-services.md)

[データベース エンジンの接続をトラブルシューティングします。](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
