---
title: Microsoft SQL Server のドライバー履歴 |Microsoft ドキュメント
ms.custom: ''
ms.date: 5/4/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: kenvh
ms.openlocfilehash: 2f2f4bafe48018da5c6f634b272a540021fd4ca2
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="driver-history-for-microsoft-sql-server"></a>Microsoft SQL Server のドライバーの履歴

このページでは、SQL Server に接続するためのマイクロソフトの履歴データの接続テクノロジについて説明します。

## <a name="odbc"></a>ODBC

SQL Server 用 Microsoft ODBC ドライバーの 3 つの異なる世代があります。 最初の"SQL Server"ODBC ドライバーは、引き続きの一部として出荷[Windows Data Access Components](#microsoft-or-windows-data-access-components)です。 このドライバーを使用して、新規の開発には推奨されません。 SQL Server 2005 以降で、 [SQL Server Native Client](#sql-server-native-client) SQL Server 2005 で SQL Server 2012 に同梱されている ODBC ドライバーであり、ODBC インターフェイスが含まれています。 このドライバーを使用して、新規の開発には推奨されません。 SQL Server 2012 以降後、 [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server)いき、最新のサーバー機能と更新されたドライバーがします。

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client は、OLE DB と ODBC の両方に使用されるスタンドアロンのライブラリです。 SQL Server Native Client (SNAC 多くの場合、省略形) は、2012 年まで SQL Server 2005 に含まれていました。 SQL Server 2005 で SQL Server 2012 で導入された新機能を利用する必要があるアプリケーションは、SQL Server Native Client を使用できます。 (Microsoft/Windows Data Access Components は更新されません SQL Server でのこれらの新機能です。)SQL Server 2012 を超える新しい機能の SQL Server Native Client は更新されません。 切り替えます Microsoft ODBC Driver の SQL Server または Microsoft OLE DB Driver for SQL Server 今後新しい SQL Server の機能を利用する場合。

SQL Server Native Client の完全なドキュメントについては、次を参照してください。、 [SQL Server Native Client のドキュメント](../relational-databases/native-client/sql-server-native-client-programming.md)です。

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver

SQL Server 2012 以降後、プライマリの ODBC driver for SQL Server を開発し、SQL Server 用 Microsoft ODBC Driver としてリリースされているがします。 詳細については、次を参照してください。、 [Microsoft ODBC Driver for SQL Server のマニュアル](./odbc/microsoft-odbc-driver-for-sql-server.md)です。

## <a name="ole-db"></a>OLE DB (OLE DB)

SQL Server の Microsoft OLE DB プロバイダーの 3 つの個別の世代があります。 一部として、最初「Microsoft OLE DB Provider for SQL Server」(SQLOLEDB) がまだ出荷[Windows Data Access Components](#microsoft-or-windows-data-access-components)です。 このプロバイダーは、新しい機能には更新されませんし、このドライバーを使用して、新規の開発をお勧めできません。 SQL Server 2005 以降で、 [SQL Server Native Client](#sql-server-native-client) SQL Server 2005 で SQL Server 2017 に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれています。 [2011年で非推奨と発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)し、このドライバーを使用して、新規の開発をお勧めできません。 2017、OLE DB データ アクセス テクノロジは、後で[undeprecated し、計画済みの新しいリリースが発表されました](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)2018年用です。 新しい OLE DB プロバイダー、"Microsoft OLE DB Driver for SQL Server"(MSOLEDBSQL) と呼びますと現在管理およびサポートされています。

## <a name="adonet"></a>ADO.NET

ADO.NET では、Microsoft .NET Framework で導入されたし、続行を改善し、管理します。 これは、Microsoft .NET Framework の主要なコンポーネントです。 詳細については、次を参照してください。 [for SQL Server の Microsoft ADO.NET](ado-net/microsoft-ado-net-for-sql-server.md)です。

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft SQL Server 用 JDBC Driver

Microsoft JDBC Driver for SQL Server 2000 で導入されたを改善し、管理を続行します。 2016 でオープン ソースがありました。 最新情報については、ドライバーをダウンロードする方法を含む、次を参照してください。 [JDBC ドライバーの概要](./jdbc/overview-of-the-jdbc-driver.md)です。

## <a name="php"></a>PHP (PHP)

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Microsoft SQL Server 用 Drivers for PHP

Microsoft Drivers for PHP for SQL Server 2009 で導入された、オープン ソース プロジェクトとしてを改善し、管理を続行します。 PHP driver のダウンロードする方法を含む、最新の情報を参照してください。 [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md)です。

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>SQL Server 用の Node.js 用の Microsoft ドライバー

Microsoft Driver for SQL Server 用の Node.js では、Microsoft Windows および Microsoft Windows Azure 上の Node.js アプリケーションを Microsoft SQL Server および Microsoft Windows Azure SQL Database へのアクセスを許可します。 開発作業は不要になったされている重点このドライバー。 Node.js 用 SQL Server の Microsoft Driver を使用して新しいアプリケーションを作成するのには推奨されません。

SQL Server 用の Node.js の Microsoft ドライバーの詳細については、次を参照してください。 [WindowsAzure/ノード sqlserver](https://github.com/Azure/node-sqlserver)です。

### <a name="tedious"></a>面倒

現在、Microsoft に寄与し、JavaScript を使用して SQL Server への接続を Node.js でオープン ソースの面倒なモジュールをサポートします。 詳細については、次を参照してください。 [Node.js Driver for SQL Server](./node-js/node-js-driver-for-sql-server.md)です。

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft アカウントまたは Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC または WDAC) に付属する Windows でサポートされるアプリケーションの旧バージョンとの互換性と、現在の SQL Server テクノロジ スタックの一部ではないです。 MDAC/WDAC 内のコンポーネントに新しい機能は追加されませんし、新しいアプリケーションの開発用に使用するには使用しないでいます。

このドキュメントの目的で、MDAC/WDAC スタックをテクノロジと製品に基づいて、次のコンポーネントに分けることができます。

* **ADO** (ADOMD と ADOX を含む)
* **OLE DB** (ODBC ドライバー、データ プロバイダー、およびリモートのデータ プロバイダーの OLE DB Core Services、SQL Server OLE DB プロバイダー、Oracle OLE DB Provider、OLE DB プロバイダーを含む)
* **ODBC** (ODBC ドライバー マネージャー、SQL ODBC ドライバーでは、Oracle ODBC ドライバーを含む)

### <a name="mdacwdac-components"></a>MDAC/WDAC コンポーネント

MDAC または WDAC には、これらのコンポーネントが含まれます。

* **ODBC:** Microsoft オープン データベース コネクティビティ) インターフェイスがさまざまなデータベース管理システム (DBMS) のデータにアクセスするアプリケーションを使用する C プログラミング言語インターフェイスです。 この API を使用するアプリケーションは、リレーショナル データ ソースのみへのアクセスに制限されます。
* **OLE DB:** OLE DB は、さまざまなデータ ストア内のデータにアクセスするための COM インターフェイスのセット。 OLE DB プロバイダーは、データベース、ファイル システム、メッセージ ストア、ディレクトリ サービス、ワークフロー、およびドキュメントのストア内のデータにアクセスするためが存在します。
* **ADO:** ActiveX データ オブジェクト (ADO) は、高度なプログラミング モデルを提供します。 パフォーマンスの高い、直接 OLE DB または ODBC をコーディングするより少ない少し ADO が簡単に理解して使用します。 これは、Microsoft Visual Basic Scripting Edition (VBScript) または Microsoft JScript などのスクリプト言語から使用できます。
* **ADOMD:** Microsoft OLAP プロバイダー、Microsoft Analysis Services プロバイダーとも呼ばれるなどの多次元データ プロバイダーで使用するのには、ADO 多次元 (ADOMD)。 主要な機能強化は行われていませんに MDAC 2.0 以降。
* **ADOX:** DDL およびセキュリティ (ADOX) 用の ADO 拡張機能が作成およびデータベース、テーブル、インデックス、またはストアド プロシージャの定義の変更を有効にします。 ADOX は、すべてのプロバイダーで使用できます。 Microsoft Jet OLE DB プロバイダーは、Microsoft SQL Server OLE DB プロバイダーには、制限付きサポートが用意されています。 ADOX、完全にサポートを提供します。
* **Microsoft SQL Server のネットワーク ライブラリ:** SQLOLEDB と SQLODBC、SQL Server データベースと通信する SQL Server のネットワーク ライブラリができるようにします。 次の SQL Server のネットワーク ライブラリが廃止された MDAC または WDAC のリリースで: Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet、および RPC。 TCP/IP および名前付きパイプをサポートするのには引き続きし、は、64 ビット Windows オペレーティング システムで使用できます。
* **MSDASQL:** Microsoft OLE DB Provider for ODBC (MSDASQL) により、ODBC ドライバーを通じてデータ ソースのアクセスを OLE DB と ADO (を内部的に、OLEDB を使用します) に基づいて構築されているアプリケーション。 MSDASQL はではなく、データベースに接続する ODBC、OLEDB プロバイダーです。 ものではブリッジとして OLE DB から ODBC ドライバーは、データ ソースの直接の OLE DB プロバイダーが存在しない場合。 MSDASQL Windows オペレーティング システムに付属していて、Windows Server 2008 および Vista SP1 された最初の Windows リリース テクノロジの 64 ビット バージョンが含まれています。

### <a name="deprecated-mdacwdac-components"></a>廃止された MDAC または WDAC コンポーネント

これらのコンポーネントは、MDAC または WDAC の現在のリリースでもサポートされますが、これらは、今後のリリースで削除する場合があります。 新しいアプリケーションを開発する場合は、これらのコンポーネントを使用しないことをお勧めします。 さらに、アップグレードまたは既存のアプリケーションを変更するときは、これらのコンポーネントに依存関係を削除します。

* **SQLOLEDB:** Microsoft OLE DB プロバイダーの SQL Server (SQLOLEDB)、Microsoft SQL Server へのアクセスをサポートするには、これは推奨されていません。 SQL Server の将来のバージョンへの接続性は、サポートされていません。 SQL Server 7 よりも前のバージョンに接続する機能は、Windows 7 の後に、オペレーティング システムから削除される予定です。 新しいアプリケーションでは、SQL Server (MSOLEDBSQL)、SQL Server の新機能をサポートする Microsoft OLE DB Driver を使用する必要があります。 既存のアプリケーションに移行 Microsoft OLE DB Driver for SQL Server も優れたパフォーマンス、信頼性、およびサポート性のです。 詳細については、次を参照してください。 [MDAC から SQL Server の OLE DB Driver をアプリケーションの更新](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)です。
* **SQLODBC:** Microsoft SQL Server ODBC ドライバー (SQLODBC)、Microsoft SQL Server へのアクセスをサポートするには、これは推奨されていません。 SQL Server の将来のバージョンへの接続性は、サポートされていません。 SQL Server 7 よりも前のバージョンに接続する機能は、Windows 7 の後に、オペレーティング システムから削除される予定です。 新しいアプリケーションでは、Windows では、SQL Server の新機能をサポートする SQL Server 用 Microsoft ODBC Driver を使用する必要があります。 既存のアプリケーションに移行 Microsoft ODBC Driver for SQL Server も優れたパフォーマンス、信頼性、およびサポート性のです。 関連する情報は、次を参照してください。 [MDAC から SQL Server Native Client へのアプリケーションの更新](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)です。
* **Microsoft Jet 4.0:** version 2.6 以降では、MDAC が存在しない Jet コンポーネントです。 つまり、MDAC 2.6、2.7、および 2.8 は、Microsoft Jet、Microsoft Jet OLE DB プロバイダー、ODBC データベース ドライバーはデスクトップ、または Jet データ アクセス オブジェクト (DAO) には含まれません。 Microsoft Jet データベース エンジンの 4.0 コンポーネントは、非推奨の機能の状態になったとエンジニア リング、持続し、Windows 2000 で Microsoft Windows のメンバーになるためレベルの機能強化を入手していません。

  64 ビット バージョンの Jet データベース エンジン、Jet ole DB ドライバー、Jet ODBC ドライバーまたは Jet DAO はありません。 詳細については、次を参照してください。[サポート技術情報記事 957570](http://support.microsoft.com/kb/957570)です。 64 ビット バージョンの Windows では、32 ビット Jet は、Windows の WOW64 サブシステムで実行されます。 WOW64 の詳細については、次を参照してください。、 [MSDN WOW64 ドキュメント](https://msdn.microsoft.com/library/windows/desktop/aa384274(v=vs.85).aspx)です。 ネイティブの 64 ビット アプリケーションは WOW64 で実行されている 32 ビット Jet ドライバーと通信できません。

  Microsoft Jet の代わりに使用をお勧めします。 [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)新規、リレーショナル データ ストアを必要とする Microsoft Access 以外のアプリケーションを開発するときにします。 これらの新しいまたは変換された Jet アプリケーションは、Microsoft Office 2003 およびそれ以前のファイル (.mdb、.xls) を使用してプライマリ以外のデータ記憶域の Jet を使用する続行できます。 ただし、これらのアプリケーションには、Jet から 2007 Office System ドライバーへの移行を計画してください。 実行できます[2007 Office System ドライバーをダウンロード](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=7554f536-8c28-4598-9b72-ef94e038c891)、Office 2003 (.mdb ファイルと .xls) または Office 2007 (読み取り、*.xlsm、*.xlsx および *.xlsb) のファイル形式のいずれかで既存のファイルを読み書きすることができます。

  > [!IMPORTANT]
  > 特定の使用法の制限に 2007 Office システムのエンド ユーザー ライセンス契約をお読みください。

  > [!NOTE]
  > SQL Server アプリケーションでは、2007 Office System をアクセスすることもと、前のファイルから SQL Server の異種データ接続と Integration Services 機能にも、2007 Office System ドライバーを使用しています。 さらに、64 ビット SQL Server アプリケーションは、64 ビット Windows で 32 ビット SQL Server Integration Services (SSIS) を使用して、32 ビット Jet と 2007 Office System ファイルにアクセスできます。

* **MSDADS:** Microsoft OLE DB プロバイダーでデータの整形 (MSDADS) のアプリケーションでキー、フィールド、または行セット間の階層リレーションシップを作成することができます。 MDAC 2.1 以降の主要な機能強化が行われていません。 このプロバイダーは廃止されました。 MSDADS ではなく、XML を使用することをお勧めします。
* **Oracle ODBC および Oracle OLE DB:** の Microsoft Oracle ODBC ドライバー (Oracle ODBC) と Microsoft OLE DB Provider for Oracle (Oracle OLE DB) は、Oracle データベース サーバーへのアクセスを提供します。 Oracle Call Interface (OCI) バージョン 7 を使用して作成された、Oracle 7 のサポートを提供します。 また、Oracle 7 エミュレーションを使用して Oracle 8 のデータベースの制限付きサポートを提供します。 Oracle では、OCI バージョン 7 の呼び出しを使用するアプリケーションがサポートされていません。 これらのテクノロジが使用されなくなりました。 Oracle データ ソースを使用している場合は、Oracle によって提供されるドライバーおよびプロバイダーに移行する必要があります。
* **RDS:** リモート データ サービス (RDS) は、インターネットまたはイントラネット経由でリモートの ADO レコード セット オブジェクトにアクセスするための独自の Microsoft メカニズムです。 RDS は廃止されました。主要な機能強化に加えられたありません RDS MDAC 2.1 以降。 Microsoft は、.NET Framework に広範な SOAP 機能を備え、RDS のコンポーネントを置き換えるをリリースしました。 RDS のすべてのサーバー コンポーネントは、Windows 7 の後に、オペレーティング システムから削除されます。
* **JRO:** Jet JRO) は推奨されなくなりました。 JRO が ADO Jet と内で使用される (*.mdb) データベースを作成し、Jet データベース (.mdb) を圧縮し、Jet レプリケーション管理を実行します。MDAC 2.7、最終リリースになります。JRO は 64 ビット Windows オペレーティング システムで使用できません。Microsoft Access 2007 のファイル形式で JRO はサポートされていません (*.accdb) です。
* **16 ビット ODBC サポート:** 16 ビット アプリケーションを使用している場合は、32 ビット アプリケーションに移行する必要があります。 16 ビットの機能は推奨されておらず、64 ビット オペレーティング システムから削除しています。 詳細については、次を参照してください。[サポート技術情報の記事 896458](http://support.microsoft.com/kb/896458)です。
* **単純な ole DB プロバイダー (MSDAOSP):** OLEDB の単純なプロバイダーは、単純なデータを OLE DB プロバイダーをすばやく構築するためのフレームワークを提供します。 MSDAOSP は推奨されません。
* **ODBC カーソル ライブラリ:** ODBC カーソル ライブラリ (ODBCCR32.dll) は、限定されたクライアント側のデータ カーソルを提供します。 ODBC カーソル ライブラリは推奨されていません。アプリケーションは、代わりに、サーバー側カーソルの実装を使用できます。
* **アウト プロセスのインターフェイスのリモート処理を OLE DB:** OLEDB インターフェイスのリモート処理 (msdaps.dll) OLE DB プロバイダーがプロセス外で実行できるようにしようとしました。 OLEDB アウト プロセスのインターフェイスのリモート処理は推奨されません。
* **AppleTalk と Banyan Vines SQL ネットワーク ライブラリ:** Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet、および RPC SQL のネットワーク ライブラリが推奨されなくなりました。 これらのテクノロジのいずれかを使用している場合は、他のネットワーク ライブラリは、TCP/IP および名前付きパイプなどのいずれかを使用するアプリケーションを変更する必要があります。

### <a name="mdacwdac-releases"></a>MDAC/WDAC リリース

次に、古いものから順の過去の MDAC/WDAC リリースのサポートのシナリオの一覧を示します。

* **MDAC 1.5 では、MDAC 2.0、および MDAC 2.1:** MDAC のこれらのバージョンが Microsoft Windows NT オプション Pack、Microsoft Windows プラットフォーム SDK、または MDAC Web サイトを介してリリースされた独立したリリースします。 MDAC のこれらのバージョンがサポートされていません。
* **MDAC 2.5:** MDAC のこのバージョンでは、Windows 2000 オペレーティング システムに含まれています。 MDAC 2.5 のサービス パックは、対応する Windows 2000 service pack に含まれていました。
* **MDAC 2.6:** MDAC 2.6 RTM、SP1、および SP2 はそれぞれ、SP1、および SP2 では、Microsoft SQL Server 2000 の RTM で含まれていた。 また、MDAC service pack は、Microsoft SQL Server 2000 サービス パックのリリースのスケジュールに従って MDAC Web サイトにリリースされました。 Windows 2000、Windows Millennium Edition、Windows NT、Windows 95 および Windows 98 プラットフォームでは、このバージョンの MDAC とそのサービス パックをインストールできます。 このバージョンの MDAC 現在はサポートされていません。
* **MDAC 2.7:** MDAC のこのバージョンでは、Microsoft Windows XP の RTM および SP1 のオペレーティング システムに付属します。 Windows 2000、Windows Millennium、Windows NT、および Windows 98 プラットフォームでは、このバージョンの MDAC とそのサービス パックをインストールできます。 オペレーティング システムまたはそのサービス パックを通じてのみ、Windows XP プラットフォームでは、このバージョンをインストールできます。 このバージョンの MDAC 現在はサポートされていません。
* **MDAC 2.8:** MDAC のこのバージョンには、Windows Server 2003 および Windows XP SP2 に含まれて以降。 また、このバージョンの MDAC とそのサービス パックを Windows 2000 にインストールすることもできます。

  * MDAC 2.8 の 32 ビット版もリリースされました MDAC Web サイトに同時に Windows Server 2003 が顧客にリリースされたこと。
  * MDAC 2.8 の 64 ビット バージョンは、Windows Server 2003 および Windows XP の 64 ビット バージョンとリリースされました。

* **Windows Data Access Components (WDAC):** MDAC WDAC -"Windows Data Access Components"Windows Vista および Windows Server 2008 以降にその名前に変更します。 WDAC では、オペレーティング システムの一部として含まれてしとは別に再配布では使用できません。 保守 WDAC では、オペレーティング システムのライフ サイクルに従います。

  WDAC の 32 ビットおよび 64 ビット バージョンがそれぞれの Windows オペレーティング システムの 32 ビットおよび 64 ビット バージョンと解放されます。

## <a name="obsolete-data-access-technologies"></a>古いデータ アクセス テクノロジ

旧式のテクノロジは、将来の製品リリースを除外していない拡張またはされたいくつかの製品リリースで更新されるテクノロジです。 新しいアプリケーションを記述するときに、これらのテクノロジを使用しないでください。 これらのテクノロジを使用して記述されている既存のアプリケーションを変更するときに、ADO.NET または現在の別のテクノロジへの移行を検討してください。

次のコンポーネントは、不使用と見なされます。

* **Db-library:** DB ライブラリは、SQL Server 固有のプログラミング モデルを C Api が含まれています。 ない DB ライブラリへの機能強化 SQL Server 6.5 以降。 SQL Server 2000 では、最終リリースの 64 ビット Windows オペレーティング システムに移植しません。
* **埋め込まれた SQL (SQL E):** E SQL では、SQL Server 固有のプログラミング モデルを Visual C のコードに埋め込まれる TRANSACT-SQL ステートメントを有効にします。 機能強化は行われていませんが E sql SQL Server 6.5 以降。 SQL Server 2000 では、最終リリースの 64 ビット Windows オペレーティング システムに移植しません。
* **データ アクセス オブジェクト (DAO):** DAO は、JET (Access) データベースへのアクセスを提供します。 この API は、Microsoft Visual Basic、Microsoft Visual C、およびスクリプト言語から使用できます。 Microsoft Office 2000 および Office XP には含まれています。 DAO 3.6 は、このテクノロジの最終バージョンです。 64 ビット Windows オペレーティング システムで利用できることはできません。
* **リモート データ オブジェクト (RDO):** RDO が、ODBC のリモートのリレーショナル データ ソースにアクセスするために設計および ODBC を使用して、複雑なアプリケーション コードを使用せずに簡単に実現します。 Microsoft Visual Basic バージョン 4、5、および 6 には含まれています。 RDO version 2.0 では、このテクノロジの最終バージョンをでした。