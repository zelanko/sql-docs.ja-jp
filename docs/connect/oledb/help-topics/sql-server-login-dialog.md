---
title: SQL Server ログイン ダイアログ ボックス (OLE DB) |Microsoft Docs
description: '[SQL Server ログイン] ダイアログ ボックス (ODBC)'
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: 4735ead33dc7c3a6d633e3b23ff1da97eeae4962
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744874"
---
# <a name="sql-server-login-dialog-box"></a>SQL Server のログイン ダイアログ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

十分な情報を指定せずに接続しようとしたときに、OLE DB ドライバーが表示されます、 **SQL Server ログイン** ダイアログ ボックス。

> [!NOTE]  
> SQL Server ログイン ダイアログ プロンプトの動作がによって制御される、`DBPROP_INIT_PROMPT`初期化プロパティ。 詳細については、以下をご覧ください。
> - [初期化プロパティと承認プロパティ](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [OLE DB プログラマ ガイド](https://go.microsoft.com/fwlink/?linkid=2067702)

![SQL Server ログイン ダイアログ ボックスのスクリーン ショット](../media/sql-server-login-dialog.png)

## <a name="options"></a>オプション
|オプション|[説明]|
|---   |---        |
|[サーバー]|ネットワーク上には、SQL Server のインスタンスの名前。 一覧から server\instance 形式の名前を選択するか、**[サーバー]** ボックスに server\instance 形式の名前を入力します。 必要に応じて、**SQL Server 構成マネージャー**を使用してクライアント コンピューターでサーバーの別名を作成し、**[サーバー]** ボックスにその名前を入力することができます。 <br/><br/>SQL Server と同じコンピューターを使用している場合は、「(local)」と入力することができます。 その後、ネットワークに接続されていない SQL Server を実行している場合でも、SQL Server のローカル インスタンスに接続することができます。<br/><br/>ネットワークのさまざまな種類のサーバー名の詳細については、次を参照してください。 [SQL Server のインストール](https://go.microsoft.com/fwlink/?linkid=2067541)します。|
|認証モード|ドロップダウン リストから、次の認証オプションを選択できます。<br/><ul><li>`Windows Authentication:` 現在のログイン ユーザーの Windows アカウントの資格情報を使用して SQL server 認証。</li><li>`SQL Server Authentication:` ログイン ID とパスワードを使用して SQL server 認証。</li><li>`Active Directory - Integrated:` 統合認証は、現在のログイン ユーザーの Windows アカウントの資格情報を使用します。</li><li>`Active Directory - Password:` Active Directory の認証ログイン ID とパスワードを使用します。</li></ul>|
|サーバー SPN|セキュリティ接続を使用する場合、サーバーのサービス プリンシパル名 (SPN) を指定できます。|
|Login ID|接続に使用するログイン ID を指定します。 ログイン ID テキスト ボックスが場合にのみ有効になって`Authentication Mode`に設定されている`SQL Server Authentication`または`Active Directory - Password`します。|
|パスワード|接続に使用されるパスワードを指定します。 パスワード テキスト ボックスは、場合にのみ`Authentication Mode`に設定されている`SQL Server Authentication`または`Active Directory - Password`します。|
|オプション|**[オプション]** グループを表示または非表示にします。 **[オプション]** ボタンは、**[サーバー]** に値が設定されている場合に有効になります。|
|パスワードの変更|により、選択した場合、**新しいパスワード**と**新しいパスワードの確認**テキスト ボックス。|
|[新しいパスワード]|新しいパスワードを指定します。|
|[新しいパスワードの確認入力]|確認のために、新しいパスワードをもう一度指定します。|
|データベース|接続で使用する既定のデータベースを指定します。 この設定は、サーバーのログインに指定されている既定のデータベースをオーバーライドします。 データベースが指定されていない場合、接続はサーバーのログインに指定されている既定のデータベースを使用します。|
|[ミラー サーバー]|ミラー化するデータベースのフェールオーバー パートナーの名前を指定します。|
|[ミラー SPN]|必要に応じて、ミラー サーバーに SPN を指定できます。 ミラー サーバーの SPN は、クライアントとサーバー間の相互認証に使用されます。|
|[言語]|SQL Server システム メッセージに使用する言語を指定します。 SQL Server を実行しているコンピューターには言語がインストールされている必要があります。 この設定は、サーバーのログインに指定されている既定の言語をオーバーライドします。 言語が指定されていない場合、接続はサーバーのログインに指定されている既定の言語を使用します。|
|Application Name|(省略可) **sys.sysprocesses** でこの接続の行の **program_name** 列にアプリケーション名が格納されるように指定します。|
|[ワークステーション ID]|(省略可) **sys.sysprocesses** でこの接続の行の **hostname** 列にワークステーション ID が格納されるように指定します。|
|[データに強力な暗号を使用する]|選択した場合、接続を介して渡されるデータは暗号化されます。|
|[サーバー証明書を信頼する]|選択した場合、サーバーの証明書が検証されます。 サーバーの証明書は、サーバーの適切なホスト名があり、信頼された証明機関によって発行されました。|

> [!NOTE]  
> 使用する場合`Windows Authentication`または`SQL Server Authentication`モード、**サーバー証明書を信頼**場合にのみと見なされます、**強力な暗号化を使用して、データの**オプションを有効にします。

## <a name="next-steps"></a>次の手順
- [Azure Active Directory 認証](../features/using-azure-active-directory.md)OLE DB ドライバーを使用します。
- セットの接続情報を使用して[Universal Data Link (UDL)](data-link-pages.md)します。