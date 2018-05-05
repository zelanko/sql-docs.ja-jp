---
title: データ ソース ウィザード画面 2 (SQL Server 用 ODBC Driver) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: v-jizho2
manager: craigg
ms.openlocfilehash: 9fc62af9910fca9f6bc5163fabdedf7bf3919b8c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-wizard-screen-2"></a>データ ソース ウィザード画面 2

認証の方法を指定し、Microsoft SQL Server アドバンスト クライアント エントリおよびログインと SQL Server 用 ODBC driver は、データ ソースの構成中に SQL Server に接続を使用してパスワードを設定します。

## <a name="options"></a>オプション

### <a name="with-integrated-windows-authentication"></a>統合 Windows 認証

ドライバーが SQL Server をセキュリティで保護された (信頼された) 接続を要求することを指定します。 オンにすると、SQL Server では、サーバーの現在のログイン セキュリティ モードに関係なく、統合ログイン セキュリティを使用して、このデータ ソースを使用する接続を確立します。 指定された任意のログイン ID またはパスワードは無視されます。 SQL Server システム管理者必要がありますが、Windows ログインに関連付けられている SQL Server ログイン ID (たとえばを使用して SQL Server Management Studio)。

必要であれば、サーバーのサービス プリンシパル名 (SPN) を指定できます。

### <a name="with-active-directory-integrated-authentication"></a>Active directory 統合認証

Azure Active Directory を使用して SQL Server へのドライバーの認証を指定します。 選択した場合、SQL Server は、サーバーでは、現在のログイン セキュリティ モードに関係なく、このデータ ソースを使用して接続を確立するために Azure Active Directory 統合ログイン セキュリティを使用します。

### <a name="with-sql-server-authentication"></a>SQL Server 認証

ログイン ID とパスワードを使用して SQL Server へのドライバーの認証を指定します。

### <a name="with-active-directory-password-authentication"></a>Active Directory パスワード認証

Azure Active Directory のログイン ID とパスワードを使用して SQL Server へのドライバーの認証を指定します。

### <a name="with-active-directory-interactive-authentication"></a>Active Directory の 対話型の認証

ログイン ID を提供することによって Azure Active Directory 対話型モードを使用して SQL Server へのドライバーの認証を指定します これにより、Windows Azure の認証プロンプト ダイアログがトリガーされます。

### <a name="login-id"></a>Login ID

ドライバーで使用する場合は、SQL Server に接続するときにログイン ID を指定**で SQL Server 認証ログイン ID と、ユーザーが入力したパスワードを使用して**または**ログイン ID を使用して Active Directory パスワードによる認証ユーザーが入力したパスワード**または**ログイン ID を使用すると Active Directory 対話型の認証がユーザーによって入力**が選択されています。 これは、サーバーの既定の設定を確認するために確立された接続のみに適用されます。そのため、データ ソースが作成された後にそのデータ ソースを使用して確立された以降の接続には適用されません。

### <a name="password"></a>Password

場合に、SQL Server に接続するときに、ドライバーを使用してパスワードを指定します**で SQL Server 認証ログイン ID と、ユーザーが入力したパスワードを使用して**または**ログイン ID を使用して Active Directory パスワードによる認証ユーザーが入力したパスワード**が選択されています。 これは、サーバーの既定の設定を確認するために確立された接続のみに適用されます。そのため、新しいデータ ソースを使用して確立された以降の接続には適用されません。

両方の**ログイン ID**と**パスワード**ボックスは使用できなくなります**で統合 Windows 認証**または**と Active Directory 統合認証**が選択されています。

### <a name="next"></a>Next

ウィザードの次の画面に進みます。

### <a name="back"></a>戻る

ウィザードの前の画面に戻ります。

## <a name="next-steps"></a>次の手順

[データ ソース ウィザード画面 1](../../../connect/odbc/windows/dsn-wizard-1.md)

[データ ソース ウィザード画面 3](../../../connect/odbc/windows/dsn-wizard-3.md)

