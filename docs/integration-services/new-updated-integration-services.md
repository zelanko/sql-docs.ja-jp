---
title: "更新済み - SQL Server 用 Integration Services のドキュメント | Microsoft Docs"
description: "Microsoft SQL Server 用 Integration Services の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: integration-services
ms.openlocfilehash: 9660fa7239c14c3adc963cc75ceb98de8316734c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>新規または最近更新: SQL Server 用 Integration Services



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 28 日**&nbsp;から &nbsp; **2017 年 12 月 2 日**
- *対象領域:* &nbsp; **SQL Server 用 Integration Services**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [オンプレミスおよび Azure のファイル共有のファイルを格納および取得する](lift-shift/ssis-azure-files-file-shares.md)
2. [Azure にデプロイされた SSIS パッケージの検証](lift-shift/ssis-azure-validate-packages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [Hadoop 接続マネージャー](#TitleNum_1)
2. [Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-hadoop-connection-managerconnection-managerhadoop-connection-managermd"></a>1.&nbsp; [Hadoop 接続マネージャー](connection-manager/hadoop-connection-manager.md)

*更新日: 2017 年 11 月 28 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 65.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2d68f4e884304f1a28045b42b680c15cc6a41ec5 fb2429466ea4d545682975d8dbea47451ce98ec7  (PR=4113  ,  Filename=hadoop-connection-manager.md  ,  Dirpath=docs\integration-services\connection-manager\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



**Kerberos 認証を使用した接続**

Hadoop 接続マネージャーで Kerberos 認証を使用できるようにオンプレミス環境を設定する方法は 2 つあります。 状況に合う方法を選択することができます。
-   方法 1: [SSIS コンピューターを Kerberos 領域に参加させる--#kerberos-join-realm)
-   方法 2: [Windows ドメインと Kerberos 領域の間の相互信頼関係を有効にする--#kerberos-mutual-trust)

**<a name="kerberos-join-realm"></a>方法 1: SSIS コンピューターを Kerberos 領域に参加させる**


**要件:**


-   ゲートウェイ コンピューターは Kerberos 領域に参加する必要があります。Windows ドメインに参加することはできません。

**構成方法:**


**SSIS コンピューター:**

1.  **Ksetup** ユーティリティを実行して、Kerberos KDC サーバーと領域を構成します。

    コンピューターはワークグループのメンバーとして構成する必要があります。これは、Kerberos 領域が Windows ドメインとは異なるためです。 次の例のように Kerberos 領域を設定し、KDC サーバーを追加します。 *REALM.COM* は、必要に応じて実際の領域に置き換えます。

```
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
```

    Restart the computer after executing these two commands.

2.  **Ksetup** コマンドを実行して構成を確認します。 出力は次の例のようになります。

```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
```

**<a name="kerberos-mutual-trust"></a>方法 2: Windows ドメインと Kerberos 領域の間の相互信頼関係を有効にする**


**要件:**

-   ゲートウェイ コンピューターは Windows ドメインに参加する必要があります。
-   ドメイン コントローラーの設定を更新するアクセス許可が必要です。

**構成方法:**


> [!NOTE]
> 次のチュートリアルの REALM.COM と AD.COM を、必要に応じて実際の領域とドメイン コントローラーに置き換えます。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authenticationlift-shiftssis-azure-connect-with-windows-authmd"></a>2.&nbsp; [Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](lift-shift/ssis-azure-connect-with-windows-auth.md)

*更新日: 2017 年 11 月 27 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1))

<!-- Source markdown line 66.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 673386fca53cb60b983e0cb3cd4b9e2ee1dee0de 65458b4dceb92d01184c5e9c6f68ec0e8f16ba08  (PR=4104  ,  Filename=ssis-azure-connect-with-windows-auth.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=19e1c4067142d33e8485cb903a7a9beb7d894015) -->



**オンプレミスの SQL Server への接続**

オンプレミスの SQL Server に接続できるかどうかを確認するには、次のことを行います。

1.  このテストを実行するには、ドメインに参加していないコンピューターを見つけます。

2.  ドメインに参加していないコンピューターで、次のコマンドを実行し、使用したいドメイン資格情報を使用して SQL Server Management Studio (SSMS) を起動します。

```
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
```

3.  SSMS から、使用するオンプレミスの SQL Server に接続できるかどうかを確認します。

**オンプレミスのファイル共有への接続**

オンプレミスのファイル共有に接続できるかどうかを確認するには、次のことを行います。

1.  このテストを実行するには、ドメインに参加していないコンピューターを見つけます。

2.  ドメインに参加していないコンピューターで、次のコマンドを実行します。 このコマンドは、使用したいドメイン資格情報を使用してコマンド プロンプト ウィンドウを開き、ディレクトリの一覧を取得することによって、ファイル共有への接続をテストします。

```
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
```

3.  使用したいオンプレミスのファイルシェアに対して、ディレクトリの一覧が返されるかどうかを確認します。

**Azure VM のファイル共有への接続**

Azure の仮想マシン上のファイル共有に接続するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のオプションの説明に従って、`catalog.set_execution_credential` ストアド プロシージャを実行します。

```
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
```

**Azure Files のファイル共有への接続**

Azure Files に関する詳細については、「[Azure ファイル](https://azure.microsoft.com/services/storage/files/)」を参照してください。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 14): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (87 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (5 + 4): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (2 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (10 + 9): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (2 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (4 + 2): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (21 + 0): **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (5 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


