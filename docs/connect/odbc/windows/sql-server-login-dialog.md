---
title: SQL Server ログイン ダイアログ ボックス (ODBC) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: v-jizho2
manager: craigg
ms.openlocfilehash: 3dcd7f9d5d3807858ae13a9ded3a2164eca20b45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-login-dialog-box-odbc"></a>[SQL Server ログイン] ダイアログ ボックス (ODBC)

ドライバーが ODBC ドライバーで、表示、SQL サーバーに接続するための十分な情報を指定せず、ODBC 接続を呼び出すと、 **SQL Server ログイン** ダイアログ ボックス。

## <a name="options"></a>オプション

### <a name="server"></a>[サーバー]

ネットワーク上の SQL Server のインスタンスの名前。 リストから、サーバー \ インスタンス名を選択するかのサーバー \ インスタンス名を入力、**サーバー**ボックス。 必要に応じて、クライアント コンピューターを使用して、サーバーの別名を作成することができます**SQL Server 構成マネージャー**でその名前を入力し、**サーバー**ボックス。

SQL Server と同じコンピューターを使用しているときに"(local)"を入力できます。 ローカル ネットワークに接続されていないバージョンの SQL Server を実行する場合でも、SQL Server のインスタンスに接続できます。

ネットワークのさまざまな種類のサーバー名の詳細については、SQL Server オンライン ブックの SQL Server のインストールに関するドキュメントを参照してください。

### <a name="authentication-mode"></a>認証モード

次のいずれかの認証モードを選択します。
- **SQL Server**ログイン ID とパスワードを使用
- **Windows 統合**現在のログイン ユーザーのアカウントを使用した認証
- **Active Directory パスワード**ログイン ID とパスワードを使用
- **Active Directory 統合**現在のログイン ユーザーのアカウントを使用した認証
- **Active Directory の 対話型**ログイン id と認証

参照してください[データ ソース ウィザード画面 2](../../../connect/odbc/windows/dsn-wizard-2.md)の詳細については、認証モードにします。

### <a name="server-spn"></a>サーバー SPN

セキュリティ接続を使用する場合、サーバーのサービス プリンシパル名 (SPN) を指定できます。

### <a name="login-id"></a>Login ID

場合、接続に使用する SQL Server または Azure Active Directory のログイン ID を指定します**認証モード**に設定されている**SQL Server**または**Active Directory パスワード**または**対話型の active Directory**です。 それ以外の場合、**ログイン ID**ボックスが無効になります。

### <a name="password"></a>Password

場合に、接続に使用される SQL Server または Azure Active Directory のログイン ID のパスワードを指定します**認証モード**に設定されている**SQL Server**または**Active Directory パスワード**。 それ以外の場合、**パスワード**ボックスが無効になります。

### <a name="options"></a>オプション

表示または非表示、**オプション**グループ。 **オプション**場合に、ボタンが有効になっている**サーバー**値を持ちます。

### <a name="change-password"></a>パスワードの変更

このボックスを選択すると、表示、**新しいパスワード**と**新しいパスワードの確認**ボックス。

### <a name="new-password"></a>[新しいパスワード]

新しいパスワードを指定します。

### <a name="confirm-new-password"></a>[新しいパスワードの確認入力]

確認のために、新しいパスワードをもう一度指定します。

### <a name="database"></a>データベース

接続で使用する既定のデータベースを指定します。 この設定は、サーバーのログインに指定されている既定のデータベースよりも優先されます。 データベースが指定されていない場合、接続はサーバーのログインに指定されている既定のデータベースを使用します。

### <a name="mirror-server"></a>[ミラー サーバー]

ミラー化するデータベースのフェールオーバー パートナーの名前を指定します。

### <a name="mirror-spn"></a>[ミラー SPN]

必要に応じて、ミラー サーバーに SPN を指定できます。 ミラー サーバーの SPN は、クライアントとサーバー間の相互認証に使用されます。

### <a name="language"></a>言語

SQL Server システム メッセージに使用する言語を指定します。 SQL Server を実行しているコンピューターには、インストールされている言語が必要です。 この設定は、サーバーのログインに指定されている既定の言語よりも優先されます。 言語が指定されていない場合、接続はサーバーのログインに指定されている既定の言語を使用します。

### <a name="application-name"></a>Application Name

(省略可能)格納されるアプリケーション名を指定します、**専用**でこの接続の行に列**sys.sysprocesses**です。

### <a name="workstation-id"></a>[ワークステーション ID]

(省略可能)格納されるワークステーション ID を指定します、 **hostname**でこの接続の行に列**sys.sysprocesses**です。

### <a name="use-strong-encryption-for-data"></a>[データに強力な暗号を使用する]

選択した場合、接続を介して渡されるデータは暗号化されます。 このチェック ボックスがオフの場合でも、既定では、ログインが暗号化されます。

### <a name="trust-server-certificate"></a>サーバー証明書を信頼します。

このオプションは、該当する場合にのみ**データに対する強力な暗号化を使用して**を有効にします。 選択した場合、サーバーの証明書は、サーバーの適切なホスト名があり、信頼された証明機関が発行するのには検証されません。

## <a name="see-also"></a>参照

[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
