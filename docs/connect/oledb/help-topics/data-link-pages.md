---
title: ユニバーサル データ リンク (UDL) の構成 |Microsoft Docs
description: Microsoft OLE DB Driver を使用して、SQL Server 用 Data Link (UDL) のユニバーサル構成
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: e198f561fd4f6bcec390ef8632c1cdc96f2810d6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62854674"
---
# <a name="universal-data-link-udl-configuration"></a>ユニバーサル データ リンク (UDL) の構成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="connection-tab"></a>[接続] タブ
[接続] タブを使用すると、SQL Server 用 Microsoft OLE DB Driver を使用して、データに接続するのに方法を指定できます。

![OLE DB データ リンク ページ - [接続] タブのスクリーン ショット](../media/data-link-pages-connection-tab.png)

[接続] タブはプロバイダー固有であり、Microsoft OLE DB Driver for SQL Server に必要な接続プロパティだけが表示されます。

|オプション|[説明]|
|---   |---        |
|[サーバー名の選択または入力]|ドロップダウン リストからサーバー名を選択するか、アクセスするデータベースが格納されているサーバーの場所を入力します。 サーバー上のデータベースを選択するのは別の操作です。 一覧を更新するには、"更新" をクリックします。
|サーバーにサインインする情報を入力します|このドロップダウン リストから、次の認証オプションを選択できます。 <ul><li>`Windows Authentication:` 現在のログイン ユーザーの Windows アカウントの資格情報を使用して SQL server 認証。</li><li>`SQL Server Authentication:` ログイン ID とパスワードを使用して SQL server 認証。</li><li>`Active Directory - Integrated:` 統合認証は、現在のログイン ユーザーの Windows アカウントの資格情報を使用します。</li><li>`Active Directory - Password:` Active Directory の認証ログイン ID とパスワードを使用します。</li></ul>|
|サーバー SPN|セキュリティ接続を使用する場合、サーバーのサービス プリンシパル名 (SPN) を指定できます。|
|[ユーザー名]|データ ソースにサインインするときに、認証に使用するユーザー ID を入力します。|
|パスワード|データ ソースにサインインするときに、認証に使用するパスワードを入力します。|
|パスワードを空白にする|選択した場合、接続文字列に空白のパスワードを使用する指定されたプロバイダーを有効にします。|
|パスワードを保存する|選択した場合、接続文字列と共に保存するためのパスワードを使用できます。 パスワードが接続文字列に含まれるかどうかは、呼び出し元アプリケーションの機能によって決まります。 <br/><br/>**注:** 保存する場合、パスワードはマスクも暗号化もされない状態で返されて保存されます。|
|[データに強力な暗号を使用する]|選択した場合、接続を介して渡されるデータは暗号化されます。|
|[サーバー証明書を信頼する]|選択した場合、サーバーの証明書が検証されます。 サーバーの証明書は、サーバーの適切なホスト名があり、信頼された証明機関によって発行されました。|
|データベースを選択する|選択するかにアクセスするデータベース名を入力します。|
|データベース ファイルをデータベース名として添付する|アタッチできるデータベースのプライマリ ファイルの名前を指定します。 このデータベースがアタッチされ、データ ソースの既定のデータベースとして使用されます。 このセクションで最初 ボックスに、アタッチされたデータベース ファイルに使用するデータベース名を入力します。<br/><br/>テキスト ボックスをオンにアタッチするデータベース ファイルへの完全パスを入力`Using the filename`、 をクリックしてまたは、`...`データベース ファイルを参照するボタンをクリックします。|
|パスワードの変更|SQL Server のパスワードの変更 ダイアログが表示されます。 |
|[接続テスト]|指定したデータ ソースへの接続を試行する をクリックします。 接続に失敗した場合、設定が正しいかどうかを確認します。 たとえば、スペル ミスや大文字と小文字の区別は接続の失敗の原因になる場合があります。|

## <a name="advanced-tab"></a>[詳細設定] タブ
詳細設定 タブを使用して、表示し、追加の初期化プロパティを設定します。

![OLE DB データ リンク ページ - 詳細設定 タブのスクリーン ショット](../media/data-link-pages-advanced-tab.png)

|オプション|[説明]|
|---   |---        |
| 接続のタイムアウト | Microsoft OLE DB Driver for SQL Server 初期化が完了するまで待機する時間 (秒) を指定します。 初期化がタイムアウトすると、エラーが返され、接続は作成されません。|


> [!NOTE]  
>  一般的なデータ リンクの接続情報を参照してください、 [Data Link API の概要](https://go.microsoft.com/fwlink/?linkid=2067432)します。

## <a name="next-steps"></a>次の手順
- [Azure Active Directory 認証](../features/using-azure-active-directory.md)OLE DB ドライバーを使用します。

- [認証の資格情報のユーザーに要求](../help-topics/sql-server-login-dialog.md)OLE DB ドライバーを使用します。