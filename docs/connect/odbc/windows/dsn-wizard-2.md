---
title: データ ソース ウィザード画面 2 (ODBC Driver for SQL Server) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 7d352b02d118c3de14cd437daf012885d7491c1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639520"
---
# <a name="data-source-wizard-screen-2"></a>データ ソース ウィザード画面 2

データ ソースの構成時に ODBC Driver for SQL Server で SQL Server への接続に使用される認証方法の指定、Microsoft SQL Server アドバンスト クライアント エントリのセットアップ、およびログインとパスワードの設定を行います。

## <a name="options"></a>[変数]

### <a name="with-integrated-windows-authentication"></a>統合 Windows 認証を使う

ドライバーが SQL Server へ接続をセキュリティで保護された (または信頼された) を要求することを指定します。 オンにすると、SQL Server では、サーバーの現在のログイン セキュリティ モードに関係なく、統合ログイン セキュリティを使用して、このデータ ソースを使用する接続を確立します。 指定された任意のログイン ID またはパスワードは無視されます。 SQL Server のシステム管理者必要がありますが、Windows ログインに関連付けられている SQL Server ログイン ID (たとえばを SQL Server Management Studio を使用)。

必要であれば、サーバーのサービス プリンシパル名 (SPN) を指定できます。

### <a name="with-active-directory-integrated-authentication"></a>Active Directory 統合認証を使用する

Azure Active Directory を使用して SQL server ドライバーを認証することを指定します。 オンにすると、SQL Server では、サーバーの現在のログイン セキュリティ モードに関係なく、Azure Active Directory 統合ログイン セキュリティを使用して、このデータ ソースを使用する接続を確立します。

### <a name="with-sql-server-authentication"></a>SQL Server 認証を使用する

ログイン ID とパスワードを使用して SQL server ドライバーを認証することを指定します。

### <a name="with-active-directory-password-authentication"></a>Active Directory パスワード認証を使用する

ドライバーが、Azure Active Directory ログイン ID とパスワードを使用して SQL server 認証を指定します。

### <a name="with-active-directory-interactive-authentication"></a>Active Directory 対話型認証を使用する

ログイン ID を提供することで、Azure Active Directory 対話型モードを使用して SQL server ドライバーを認証することを指定します。 これにより、Windows Azure の認証プロンプト ダイアログがトリガーされます。

### <a name="login-id"></a>Login ID

場合は、SQL Server に接続するときに、ドライバーを使用してログイン ID を指定します**で SQL Server 認証ログイン ID と、ユーザーが入力したパスワードを使用して**または**で Active Directory パスワード認証のログイン ID を使用します。ユーザーが入力したパスワードと**または**で Active Directory 対話型認証ログイン ID を使用してユーザーの入力**が選択されています。 これは、サーバーの既定の設定を確認するために確立された接続のみに適用されます。そのため、データ ソースが作成された後にそのデータ ソースを使用して確立された以降の接続には適用されません。

### <a name="password"></a>パスワード

場合は、SQL Server に接続するときに、ドライバーを使用してパスワードを指定します**で SQL Server 認証ログイン ID と、ユーザーが入力したパスワードを使用して**または**で Active Directory パスワード認証のログイン ID を使用します。ユーザーが入力したパスワードと**が選択されています。 これは、サーバーの既定の設定を確認するために確立された接続のみに適用されます。そのため、新しいデータ ソースを使用して確立された以降の接続には適用されません。

両方の**ログイン ID**と**パスワード**場合、ボックスは無効になっている**で統合 Windows 認証**または**で Active Directory 統合認証**が選択されています。

### <a name="next"></a>Next

ウィザードの次の画面に進みます。

### <a name="back"></a>戻る

ウィザードの前の画面に戻ります。

## <a name="next-steps"></a>次の手順

[データ ソース ウィザード画面 1](../../../connect/odbc/windows/dsn-wizard-1.md)

[データ ソース ウィザード画面 3](../../../connect/odbc/windows/dsn-wizard-3.md)

