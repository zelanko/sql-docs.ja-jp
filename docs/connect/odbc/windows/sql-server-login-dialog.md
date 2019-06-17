---
title: SQL Server ログイン ダイアログ ボックス (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: v-jizho2
manager: jroth
ms.openlocfilehash: 2d7cf1f31ce5cf42b9c2e4c7b72938b8def2ed4f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797736"
---
# <a name="sql-server-login-dialog-box-odbc"></a>[SQL Server ログイン] ダイアログ ボックス (ODBC)

ドライバーが SQL Server に接続するのに十分な情報を指定せずに ODBC 接続を呼び出すと、ODBC ドライバーにより、 **[SQL Server ログイン]** ダイアログ ボックスが表示されます。

## <a name="options"></a>オプション

### <a name="server"></a>[サーバー]

ネットワーク上には、SQL Server のインスタンスの名前。 一覧から server\instance 形式の名前を選択するか、 **[サーバー]** ボックスに server\instance 形式の名前を入力します。 必要に応じて、**SQL Server 構成マネージャー**を使用してクライアント コンピューターでサーバーの別名を作成し、 **[サーバー]** ボックスにその名前を入力することができます。

SQL Server と同じコンピューターを使用している場合は、「(local)」と入力することができます。 その後、ネットワークに接続されていない SQL Server を実行している場合でも、SQL Server のローカル インスタンスに接続することができます。

さまざまな種類のネットワークに対応するサーバー名の詳細については、SQL Server オンライン ブックにある SQL Server のインストールに関するドキュメントを参照してください。

### <a name="authentication-mode"></a>認証モード

次のいずれかから認証モードを選択します。
- **SQL Server**ログイン ID とパスワード
- **Windows 統合**現在のログイン ユーザーのアカウントを使った認証
- **Active Directory パスワード**ログイン ID とパスワード
- **Active Directory 統合**現在のログイン ユーザーのアカウントを使った認証
- ログイン ID を使用した **Active Directory 対話型**認証

参照してください[データ ソース ウィザード画面 2](../../../connect/odbc/windows/dsn-wizard-2.md)認証モードの詳細についてはします。

### <a name="server-spn"></a>サーバー SPN

セキュリティ接続を使用する場合、サーバーのサービス プリンシパル名 (SPN) を指定できます。

### <a name="login-id"></a>Login ID

場合、接続に使用する SQL Server または Azure Active Directory のログイン ID を指定します**認証モード**に設定されている**SQL Server**または**Active Directory パスワード**または**Active Directory 対話型**します。 それ以外の場合、**ログイン ID**ボックスが無効になります。

### <a name="password"></a>パスワード

場合に、接続に使用される SQL Server または Azure Active Directory のログイン ID のパスワードを指定します**認証モード**に設定されている**SQL Server**または**Active Directory パスワード。** . それ以外の場合、**パスワード**ボックスが無効になります。

### <a name="options"></a>オプション

**[オプション]** グループを表示または非表示にします。 **[オプション]** ボタンは、 **[サーバー]** に値が設定されている場合に有効になります。

### <a name="change-password"></a>パスワードの変更

このチェック ボックスをオンにすると、 **[新しいパスワード]** ボックスと **[新しいパスワードの確認入力]** ボックスが表示されます。

### <a name="new-password"></a>[新しいパスワード]

新しいパスワードを指定します。

### <a name="confirm-new-password"></a>[新しいパスワードの確認入力]

確認のために、新しいパスワードをもう一度指定します。

### <a name="database"></a>データベース

接続で使用する既定のデータベースを指定します。 この設定は、サーバーのログインに指定されている既定のデータベースをオーバーライドします。 データベースが指定されていない場合、接続はサーバーのログインに指定されている既定のデータベースを使用します。

### <a name="mirror-server"></a>[ミラー サーバー]

ミラー化するデータベースのフェールオーバー パートナーの名前を指定します。

### <a name="mirror-spn"></a>[ミラー SPN]

必要に応じて、ミラー サーバーに SPN を指定できます。 ミラー サーバーの SPN は、クライアントとサーバー間の相互認証に使用されます。

### <a name="language"></a>[言語]

SQL Server システム メッセージに使用する言語を指定します。 SQL Server を実行しているコンピューターには言語がインストールされている必要があります。 この設定は、サーバーのログインに指定されている既定の言語をオーバーライドします。 言語が指定されていない場合、接続はサーバーのログインに指定されている既定の言語を使用します。

### <a name="application-name"></a>Application Name

(省略可) **sys.sysprocesses** でこの接続の行の **program_name** 列にアプリケーション名が格納されるように指定します。

### <a name="workstation-id"></a>[ワークステーション ID]

(省略可) **sys.sysprocesses** でこの接続の行の **hostname** 列にワークステーション ID が格納されるように指定します。

### <a name="use-strong-encryption-for-data"></a>[データに強力な暗号を使用する]

選択した場合、接続を介して渡されるデータは暗号化されます。 このチェック ボックスがオフの場合でも、既定では、ログインが暗号化されます。

### <a name="trust-server-certificate"></a>[サーバー証明書を信頼する]

このオプションは、該当する場合にのみ**強力な暗号化を使用して、データの**を有効にします。 選択した場合、サーバーの証明書は、サーバーの適切なホスト名があり、信頼された証明書機関から発行するのには検証されません。

## <a name="see-also"></a>参照

[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
