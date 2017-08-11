---
title: "ODBC データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6318776-a188-48a7-995d-9eafd7148ff2
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4d1a2374d480f2d6b886425a02cb590b00b3564a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-odbc-data-source-sql-server-import-and-export-wizard"></a>ODBC データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **ODBC**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。

Microsoft から必要があるか、サードパーティ製の ODBC ドライバーをダウンロードする必要があります。

指定する必要がある必要な接続情報を検索することもあります。 このサード パーティ サイト -[この接続文字列参照には](https://www.connectionstrings.com/)-サンプルの接続文字列とデータ プロバイダーに関する詳細な情報と必要な接続情報が含まれます。

## <a name="make-sure-the-driver-you-want-is-installed"></a>インストールされている場合、ドライバーを確認してください。
1.  検索または参照する、 **ODBC データ ソース (64 ビット)**コントロール パネルのアプレットします。 32 ビット ドライバーのみがあるか、32 ビット ドライバーを使用することがわかっている場合を検索するか参照**ODBC データ ソース (32 ビット)**代わりにします。
2.  アプレットを起動します。 **ODBC データ ソース アドミニストレーター**ウィンドウが開きます。
3.  **ドライバー**  タブ、お使いのコンピューターにインストールされているすべての ODBC ドライバーの一覧を見つけることができます。 (一部のドライバーの名前は、複数の言語で表示する可能性があります)。

    インストールされている 64 ビット ドライバーの一覧の例を次に示します。

    ![64 ビット ODBC ドライバーのインストール](../../integration-services/import-export-data/media/installed-64-bit-odbc-drivers.png)

> [!TIP]
> ドライバーのインストールされ、64 ビット アプレットに表示されないことがわかっている場合は、32 ビット アプレットで代わりに検索します。 これも示します、64 ビットまたは 32 ビット SQL Server インポートおよびエクスポート ウィザードを実行する必要があるかどうか。
    
## <a name="step-1---select-the-data-source"></a>手順 1 - データ ソースの選択
お使いのコンピューターにインストールされている ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 ODBC ドライバーで接続するを選択して開始、 **.NET Framework Data Provider for ODBC**上のデータ ソースとして、**データ ソースを選択**または**先選択**ウィザードのページです。 このプロバイダーは、ODBC ドライバーをラップするラッパーとして機能します。

ここで、odbc、.NET Framework Data Provider を選択した後すぐに表示されているジェネリック画面です。

![前に odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

## <a name="step-2---provide-the-connection-info"></a>手順 2 - 接続情報を指定します
次の手順では、ODBC ドライバーと、データ ソースの接続情報を提供します。 この場合、2 つの選択肢があります。
1.  提供、 **DSN** (データ ソース名) を既に存在するか、使用して作成した、 **ODBC データ ソース アドミニストレーター**コントロール パネルのアプレットします。 DSN は、ODBC データ ソースへの接続に必要な設定の保存済みのコレクションです。

    既に DSN の名前を知っているか、今すぐ新しい DSN を作成する方法を理解する場合、は、このページの残りの部分を省略できます。 DSN 名を入力します、 **Dsn**フィールドに、**データ ソースを選択**または**変換先を選択**ページ、ウィザードの次の手順を続行しています。

    [DSN を提供します。](#odbc_dsn)
    
2.  提供、**接続文字列**、online を検索または作成し、使用してコンピューター上でテスト、する、 **ODBC データ ソース アドミニストレーター**アプレットします。

    既にまたはした場合は、接続文字列を作成する方法を知っている、このページの残りの部分を省略できます。 接続文字列を入力、 **ConnectionString**フィールドに、**データ ソースを選択**または**変換先を選択**ページ、ウィザードの次の手順を続行しています。

    [接続文字列を指定します。](#odbc_connstring)

接続文字列を指定した場合、**データ ソースを選択**または**変換先の選択**ページ、ウィザードを使用してサーバーとデータベースの名前と認証方法など、データ ソースに接続する予定のすべての接続情報が表示されます。 DSN を指定すると、この情報は表示されません。

## <a name="odbc_dsn"></a>オプション 1 - DSN の提供
DSN (データ ソース名) で接続情報を提供する場合は、使用、 **ODBC データ ソース アドミニストレーター**アプレット既存の DSN の名前を検索するか、新しい DSN を作成します。
1.  検索または参照する、 **ODBC データ ソース (64 ビット)**コントロール パネルのアプレットします。 のみまたはした場合、32 ビット ドライバーを 32 ビット ドライバーを使用する必要がある、検索するか参照**ODBC データ ソース (32 ビット)**代わりにします。
2.  アプレットを起動します。 **ODBC データ ソース アドミニストレーター**ウィンドウが開きます。 アプレットは次のようになります。

    ![コントロール パネルの odbc データ ソース アドミニストレーター](../../integration-services/import-export-data/media/odbc-administrator-control-panel-applet.png)
    
3.  する場合**既存の DSN を使用して**、データ ソースに表示される任意の DSN を使用することができます、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブです。 名前を確認し、ウィザードに戻ってに入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先の選択**ページ。 このページの残りの部分をスキップし、ウィザードの次の手順を続行します。
4.  する場合**新しい DSN を作成する**表示されるようにするかどうかにのみ (ユーザー DSN)、コンピューターのすべてのユーザーに表示されるなどの Windows サービスの (システム DSN) を決定する、または (ファイル DSN) のファイルに保存します。 この例では、新しいシステム DSN を作成します。
5. **システム DSN**  タブで、をクリックして**追加**です。

    ![新しい ODBC システム DSN を追加します。](../../integration-services/import-export-data/media/add-a-new-odbc-system-dsn.png)
    
6.  **新しいデータ ソースを作成**ダイアログ ボックスでは、データ ソースのドライバーを選択し、をクリックして**完了**です。

    ![新しいシステム DSN のドライバーを選択します。](../../integration-services/import-export-data/media/pick-driver-for-new-system-dsn.png)
    
7. ドライバーでは、データ ソースへの接続に必要な情報を入力する 1 つまたは複数ドライバー固有の画面が表示されます。 (SQL Server のドライバーのなどがあるカスタム設定の 4 つのページ)完了したら、新しいシステム DSN が一覧に表示します。

    ![一覧に新しいシステム DSN](../../integration-services/import-export-data/media/new-system-dsn-in-list.png)
    
8.  ウィザードに戻り、DSN 名を入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先の選択**ページ。 ウィザードの次の手順に進みます。

## <a name="odbc_connstring"></a>オプション 2 - 接続文字列を指定
接続文字列を使用して接続情報を指定する場合は、このトピックの残りの部分が必要な接続文字列を取得できます。

この例は、Microsoft SQL Server に接続する次の接続文字列を使用しようとしています。

    Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;

内の接続文字列を入力、 **ConnectionString**フィールドに、**データ ソースを選択**または**変換先の選択**ページ。 接続文字列を入力すると後、ウィザードは、文字列を解析し、個々 のプロパティとその値を一覧に表示します。

ここで、接続文字列を入力した後に表示される画面です。

![後の odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

> [!NOTE]
> ODBC ドライバーの接続オプションは、ソースまたは変換先を構成しているかどうかに、同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

## <a name="get-the-connection-string-online"></a>オンライン接続文字列を取得します。
ODBC ドライバーをオンラインの接続文字列が見つかりませんを参照してください。[この接続文字列参照には](https://www.connectionstrings.com/)します。 このサード パーティのサイトには、サンプルの接続文字列とデータ プロバイダーの詳細と必要な接続情報が含まれています。

## <a name="get-the-connection-string-with-an-app"></a>アプリに接続文字列を取得します。
使用することができますをビルドし、自分のコンピューターで、ODBC ドライバーの接続文字列をテスト、 **ODBC データ ソース アドミニストレーター**コントロール パネルのアプレットします。 ファイル DSN、接続を作成し、ファイル DSN、接続文字列をアセンブルする外の設定をコピーします。 これにより、いくつかの手順が必要ですが、有効な接続文字列があるかどうかを確認するのに役立ちます。

1.  検索または参照する、 **ODBC データ ソース (64 ビット)**コントロール パネルのアプレットします。 のみまたはした場合、32 ビット ドライバーを 32 ビット ドライバーを使用する必要がある、検索するか参照**ODBC データ ソース (32 ビット)**代わりにします。
2.  アプレットを起動します。 **ODBC データ ソース アドミニストレーター**ウィンドウが開きます。
3.  次に「、**ファイル DSN**アプレットの [] タブ。 **[追加]**をクリックします。

    この例では、ファイル DSN、接続文字列に必要な特定の形式で名前と値のペアを保存するためにファイル DSN ではなく、ユーザー DSN またはシステム DSN を作成します。

    ![新しい ODBC ファイル DSN を追加します。](../../integration-services/import-export-data/media/add-a-new-odbc-file-dsn.png)

4.  **データ ソースの新規作成**ダイアログ ボックスでは、一覧で、ドライバを選択し、をクリックして**次**です。 この例は、Microsoft SQL Server に接続する必要があります。 接続文字列引数を格納する DSN を作成中です。

    ![新しい ODBC データ ソースを作成します。](../../integration-services/import-export-data/media/create-new-odbc-data-source.png)
    
5.  場所を選択して、新しいファイル DSN の名前を入力し、をクリックして**次**です。 それを検索して後続の手順で開いたようにファイルを保存する場所を覚えておいてください。

    ![新しいファイル DSN を保存します。](../../integration-services/import-export-data/media/save-new-file-dsn.png)

6.  選択内容の概要を確認し、をクリックして**完了**です。

7.  クリックした後**完了**、選択したドライバーが接続する必要がある情報を収集する 1 つまたは複数の独自の画面を表示します。 通常この情報には、サーバー、ログイン情報、およびサーバー ベースのデータ ソース、およびファイル、形式、およびファイル ベースのデータ ソースのバージョンのデータベースが含まれます。

8. データ ソースを構成し、をクリックした後**完了**、通常選択内容の概要を表示され、それらをテストするチャンスがあります。

    ![新しいファイル DSN のテスト](../../integration-services/import-export-data/media/test-new-file-dsn.png)

9. データ ソースをテストしてダイアログ ボックスを閉じて後からファイル システムに保存ファイル DSN を検索します。 ファイル拡張子を変更していない、既定の拡張子はします。DSN。

10. メモ帳または別のテキスト エディターで、保存したファイルを開きます。 この SQL Server の例の内容を次に示します。

        [ODBC]  
        DRIVER=ODBC Driver 13 for SQL Server  
        TrustServerCertificate=No  
        DATABASE=WideWorldImporters    
        WSID=<local computer name>  
        APP=Microsoft® Windows® Operating System  
        Trusted_Connection=Yes  
        SERVER=localhost   
        
11. コピーし、名前と値のペアがセミコロンで区切られた接続文字列に必要な値を貼り付けます。

    サンプル ファイル DSN から必要な値を作成すると、次の接続文字列があります。
    
        DRIVER=ODBC Driver 13 for SQL Server;SERVER=localhost;DATABASE=WideWorldImporters;Trusted_Connection=Yes

    すべての設定を操作する接続文字列を作成する ODBC データ ソース アドミニストレーターによって作成された DSN で通常必要はありません。  
    -   常に、ODBC ドライバーを指定する必要があるとします。
    -   SQL Server のようなサーバー ベースのデータ ソースの場合、通常必要サーバー、データベース、およびログイン情報。 サンプルでは、DSN、TrustServerCertificate、WSID、またはアプリが不要です。
    -   ファイル ベースのデータ ソースの場合は、名前と場所には、少なくともファイルする必要があります。
    
12. この接続文字列を貼り付けたり、 **ConnectionString**フィールドに、**データ ソースを選択**または**変換先の選択**ウィザードのページです。 ウィザードが、文字列を解析し、続行する準備ができました!

    ![後の odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)



