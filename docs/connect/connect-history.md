---
title: Microsoft SQL Server のドライバーの履歴 |Microsoft Docs
ms.custom: ''
ms.date: 05/04/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f8a0c12939882602f21a849d2fb3ec7d829df92b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822772"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Microsoft SQL Server のドライバーの履歴

このページには、SQL Server に接続するためのマイクロソフトの履歴データの接続テクノロジについて説明します。

## <a name="odbc"></a>ODBC

SQL Server 用 Microsoft ODBC ドライバーには 3 つの異なる世代があります。 最初の"SQL Server"ODBC ドライバーの一部としても出荷[Windows Data Access Components](#microsoft-or-windows-data-access-components)します。 このドライバーを使用して、新規の開発には推奨されません。 SQL Server 2005 以降、 [SQL Server Native Client](#sql-server-native-client) SQL Server 2005 から SQL Server 2012 に同梱されている ODBC ドライバーであり、ODBC インターフェイスが含まれています。 このドライバーを使用して、新規の開発には推奨されません。 SQL Server 2012 では、以降後、 [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server)は今後、最新のサーバー機能と更新されたドライバー。

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client は、OLE DB と ODBC の両方に使用されるスタンドアロン ライブラリです。 SQL Server Native Client (SNAC 多くの場合、省略形) は、2012 年までに SQL Server 2005 に含まれていました。 SQL Server Native Client は、SQL Server 2005 から SQL Server 2012 で導入された新機能を活用するために必要とするアプリケーションで使用できます。 (Microsoft/Windows Data Access Components は SQL Server でのこれらの新機能の更新されません)。SQL Server 2012 を超える新しい機能については、SQL Server Native Client は更新されません。 切り替える Microsoft ODBC Driver for SQL Server または Microsoft OLE DB Driver for SQL Server の新しい SQL Server 機能が今後利用する場合。

SQL Server Native Client の完全なドキュメントについては、次を参照してください。、 [SQL Server Native Client のドキュメント](../relational-databases/native-client/sql-server-native-client-programming.md)します。

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver

SQL Server 2012 では後、プライマリ ODBC driver for SQL Server を開発し、SQL Server 用 Microsoft ODBC Driver としてリリースされています。 詳細については、次を参照してください。、 [Microsoft ODBC Driver for SQL Server のドキュメント](./odbc/microsoft-odbc-driver-for-sql-server.md)します。

## <a name="ole-db"></a>OLE DB (OLE DB)

SQL Server 向けの Microsoft OLE DB プロバイダーには 3 つの世代があります。 最初の "Microsoft OLE DB Provider for SQL Server" (SQLOLEDB) は、現在でも [Windows Data Access Components](#microsoft-or-windows-data-access-components) の一部として同梱されています。 このプロバイダーは、新機能では更新されませんし、このドライバーを使用して、新規の開発をお勧めできません。 SQL Server 2005 以降、 [SQL Server Native Client](#sql-server-native-client)から SQL Server 2017 までの SQL Server 2005 に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれています。 [2011 年に非推奨として発表済み](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)であり、新規開発にこのドライバーを使用することはお勧めしません。 OLE DB データ アクセス テクノロジをその後が 2017年では、[取り消すと、新しい計画的なリリースが発表されました](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)2018 年。 新しい OLE DB プロバイダーは、"Microsoft OLE DB Driver for SQL Server"(MSOLEDBSQL) とは現在保持し、呼ばサポートされています。

## <a name="adonet"></a>ADO.NET

ADO.NET は、Microsoft .NET Framework で導入され、引き続き改善され、維持します。 Microsoft .NET Framework の主要なコンポーネントになります。 詳細については、次を参照してください。 [SQL Server 向けの Microsoft ADO.NET](ado-net/microsoft-ado-net-for-sql-server.md)します。

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft SQL Server 用 JDBC Driver

2000 で導入された、Microsoft JDBC Driver for SQL Server は引き続き改善され、維持します。 2016 でオープン ソース化でした。 ドライバーをダウンロードする方法など、最新の情報を参照してください。 [JDBC ドライバーの概要](./jdbc/overview-of-the-jdbc-driver.md)します。

## <a name="php"></a>PHP (PHP)

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Microsoft SQL Server 用 Drivers for PHP

2009 で導入された、オープン ソース プロジェクトとして、Microsoft Drivers for PHP for SQL Server は引き続き改善され、維持されます。 PHP のドライバーをダウンロードする方法など、最新の情報を参照してください。 [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md)します。

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Microsoft Driver for Node.js for SQL Server

Microsoft Driver for Node.js for SQL Server では、Microsoft SQL Server および Microsoft Windows Azure SQL Database にアクセスする Microsoft Windows と Microsoft Windows Azure で Node.js アプリケーションを使用します。 このドライバーでは、開発作業が絞りできなくします。 For Node.js for SQL Server、Microsoft ドライバーを使用して新しいアプリケーションを作成することは推奨されません。

詳細については、Microsoft Driver for Node.js for SQL Server を参照してください。 [WindowsAzure/ノード sqlserver](https://github.com/Azure/node-sqlserver)します。

### <a name="tedious"></a>面倒です

Microsoft は現在に貢献して、オープン ソースの面倒なモジュールを Node.js で JavaScript を使用して SQL Server への接続をサポートしています。 詳細については、次を参照してください。 [Node.js Driver for SQL Server](./node-js/node-js-driver-for-sql-server.md)します。

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft または Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC または WDAC) に付属するサポートされている Windows でアプリケーションの下位互換性と、現在の SQL Server テクノロジ スタックの一部ではないです。 MDAC/WDAC 内のコンポーネントに新しい機能は追加されませんし、新しいアプリケーションの開発に使用するには使用しないでいます。

このドキュメントの目的で、テクノロジと製品に基づいて、次のコンポーネント MDAC/WDAC スタックに分割することができます。

* **ADO** (ADOMD と ADOX を含む)
* **OLE DB** (ODBC ドライバー、データ プロバイダー、およびリモートのデータ プロバイダー、OLE DB Core Services、SQL Server OLE DB プロバイダー、Oracle OLE DB Provider、OLE DB プロバイダーを含む)
* **ODBC** (ODBC ドライバー マネージャー、SQL ODBC ドライバーでは、Oracle ODBC ドライバーを含む)

### <a name="mdacwdac-components"></a>MDAC/WDAC コンポーネント

MDAC または WDAC には、これらのコンポーネントが含まれています。

* **ODBC:** Microsoft Open Database Connectivity (ODBC) インターフェイスは、さまざまなデータベース管理システム (DBMS) のデータにアクセスするアプリケーションを使用する C プログラミング言語インターフェイス。 この API を使用するアプリケーションは、リレーショナル データ ソースのみへのアクセスに制限されます。
* **OLE DB:** OLE DB は、さまざまなデータ ストア内のデータにアクセスするための COM インターフェイスのセット。 データベース、ファイル システム、メッセージ ストア、ディレクトリ サービス、ワークフロー、およびドキュメント ストア内のデータにアクセスするための OLE DB プロバイダーが存在します。
* **ADO:** ActiveX Data Objects (ADO)、高度なプログラミング モデルを提供します。 OLE DB または ODBC を直接コーディングよりパフォーマンスが向上より少し ADO が簡単に理解して使用します。 これは、Microsoft Visual Basic Scripting Edition (VBScript) または Microsoft JScript などのスクリプト言語から使用できます。
* **ADOMD:** .ADO 多次元 (ADOMD) では、Microsoft Analysis Services プロバイダーとも呼ばれる Microsoft OLAP プロバイダーなどの多次元データ プロバイダーで使用します。 主要な機能強化がない以降に加え、MDAC 2.0。
* **ADOX:** DDL およびセキュリティ (ADOX) 用の ADO 拡張機能を作成し、データベース、テーブル、インデックス、またはストアド プロシージャの定義を変更します。 ADOX は、任意のプロバイダーで使用できます。 Microsoft Jet OLE DB プロバイダーは、制限付きサポートを提供しますが、Microsoft SQL Server OLE DB プロバイダーの ADOX、完全にサポートを提供します。
* **Microsoft SQL Server のネットワーク ライブラリ:** SQLOLEDB と SQLODBC、SQL Server データベースと通信する SQL Server のネットワーク ライブラリを許可します。 次の SQL Server のネットワーク ライブラリが非推奨とされました MDAC/WDAC のリリースで: Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet、および RPC。 TCP/IP および名前付きパイプは引き続きサポートされ、64 ビット Windows オペレーティング システムでは使用できます。
* **MSDASQL:** Microsoft OLE DB Provider for ODBC (MSDASQL) は、ODBC ドライバーを通じてデータ ソースのアクセスを OLE DB と ADO (内部的に OLEDB を使用) する上で構築されるアプリケーションをできます。 MSDASQL はデータベースの代わりに、ODBC に接続する OLEDB プロバイダーです。 ものでは、ブリッジから OLE DB、ODBC ドライバーにデータ ソースの直接の OLE DB プロバイダーが存在しない場合。 MSDASQL は、Windows オペレーティング システムが付属していて、Windows Server 2008 および Vista SP1 が最初の Windows リリース テクノロジの 64 ビット バージョンが含まれます。

### <a name="deprecated-mdacwdac-components"></a>非推奨の MDAC/WDAC コンポーネント

これらのコンポーネントは引き続き MDAC または WDAC の現在のリリースでサポートされますが、今後のリリースでは削除される可能性があります。 新しいアプリケーションを開発するには、Microsoft では、これらのコンポーネントを使用しないことをお勧めします。 さらに、アップグレードするか、既存のアプリケーションを変更するときに、これらのコンポーネントへの依存関係を削除します。

* **SQLOLEDB:** Microsoft OLE DB Provider for SQL Server (SQLOLEDB)、Microsoft SQL Server へのアクセスをサポートするには、これは非推奨とされました。 SQL Server の将来のバージョンへの接続性は、サポートされていません。 SQL Server 7 より前のバージョンに接続する機能は、Windows 7 の後に、オペレーティング システムから削除される予定です。 新しいアプリケーションは、Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)、新しい SQL Server の機能をサポートするを使用する必要があります。 既存のアプリケーションに移行 Microsoft OLE DB Driver for SQL Server も優れたパフォーマンス、信頼性、およびサポート性の。 詳細については、次を参照してください。 [MDAC から SQL Server の OLE DB ドライバーへのアプリケーションの更新](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)します。
* **SQLODBC:** Microsoft SQL Server ODBC ドライバー (SQLODBC)、Microsoft SQL Server へのアクセスをサポートするには、これは非推奨とされました。 SQL Server の将来のバージョンへの接続性は、サポートされていません。 SQL Server 7 より前のバージョンに接続する機能は、Windows 7 の後に、オペレーティング システムから削除される予定です。 新しいアプリケーションでは、新しい SQL Server の機能をサポートする、Windows 上の SQL Server の Microsoft ODBC Driver を使用する必要があります。 既存のアプリケーション移行に Microsoft ODBC Driver for SQL Server も優れたパフォーマンス、信頼性、およびサポート性のください。 関連する情報は、次を参照してください。 [MDAC から SQL Server Native Client へアプリケーションの更新](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)します。
* **Microsoft Jet データベース エンジン 4.0:** バージョン 2.6 以降、MDAC が Jet コンポーネント。 つまり、MDAC 2.6 や 2.7、2.8 は、Microsoft Jet、Microsoft Jet OLE DB プロバイダー、ODBC デスクトップ データベース ドライバー、または Jet データ アクセス オブジェクト (DAO) には含まれません。 

  Jet データベース エンジン、Jet OLEDB ドライバー、Jet ODBC ドライバー、または Jet DAO の 64 ビット バージョンはありません。 詳細については、[サポート技術情報の記事 957570](https://support.microsoft.com/kb/957570) を参照してください。 Windows の 64 ビット バージョンでは、32 ビットの Jet は、Windows の WOW64 サブシステムで実行されます。 WOW64 の詳細については、次を参照してください。、 [MSDN WOW64 ドキュメント](/windows/desktop/WinProg64/wow64-implementation-details)します。 ネイティブの 64 ビット アプリケーションは WOW64 で実行されている 32 ビットの Jet ドライバーと通信できません。

  Microsoft Jet では、代わりに使用をお勧めします。 [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)新規、リレーショナル データ ストアを必要とする Microsoft Access 以外のアプリケーションを開発するときにします。 非プライマリ データ ストレージ用の Microsoft Office 2003 およびそれ以前のファイル (.mdb ファイルと .xls) を使用して Jet を使用するこれら新しいと、変換後の Jet アプリケーションを続行できます。 ただし、これらのアプリケーション Jet からは Microsoft Access データベース エンジンへの移行を計画する必要があります。 できます[は Microsoft Access データベース エンジンをダウンロード](https://www.microsoft.com/download/details.aspx?id=54920)からの読み取りを Office 2003 (.mdb ファイルと .xls) または Office 2007 (*.accdb、*.xlsm、*.xlsx および *.xlsb) のファイル形式のいずれかで既存のファイルに書き込むことのできます。

  > [!IMPORTANT]
  > 特定の使用量の制限については 2007 Office System のエンド ユーザー ライセンス契約をお読みください。

  > [!NOTE]
  > SQL Server アプリケーションは、2007 Office System にアクセスできることもおよび以前では、ファイルから SQL Server の異種データ接続と Integration Services 機能にも、2007 Office System ドライバーを経由しています。 さらに、64 ビット SQL Server のアプリケーションは、64 ビット Windows で 32 ビット SQL Server Integration Services (SSIS) を使用して、32 ビットの Jet と 2007 Office System のファイルにアクセスできます。

* **MSDADS:** Microsoft OLE DB プロバイダーでデータの整形 (MSDADS) のアプリケーションでキー、フィールド、または行セット間の階層リレーションシップを作成することができます。 MDAC 2.1 以降の主要な機能強化が行われていません。 このプロバイダーは非推奨とされました。 MSDADS ではなく、XML を使用することをお勧めします。
* **Oracle ODBC および Oracle OLE DB:** The Microsoft Oracle ODBC ドライバー (Oracle ODBC) と Microsoft OLE DB Provider for Oracle (Oracle OLE DB) は、Oracle データベース サーバーへのアクセスを提供します。 Oracle Call Interface (OCI) バージョン 7 を使用して作成された、Oracle 7 の完全なサポートを提供します。 また、Oracle 7 エミュレーションを使用して Oracle 8 データベースの制限付きサポートを提供します。 Oracle は、OCI バージョン 7 の呼び出しを使用するアプリケーションをサポートしていません。 これらのテクノロジが非推奨とされます。 Oracle データ ソースを使用している場合は、Oracle によって提供されるドライバーおよびプロバイダーに移行する必要があります。
* **RDS:** リモート データ サービス (RDS) は、インターネットまたはイントラネットの間でリモートの ADO レコード セット オブジェクトにアクセスするための独自の Microsoft メカニズムです。 RDS で非推奨とされます。主要な機能が強化されてありません RDS MDAC 2.1 以降。 マイクロソフトは、.NET Framework は、SOAP の幅広い機能を備え、RDS のコンポーネントを置き換えるをリリースしました。 すべての RDS サーバー コンポーネントは、Windows 7 の後に、オペレーティング システムから削除されます。
* **JRO:** Jet JRO) が非推奨とされます。 JRO は Jet で ADO で使用されます ( *.mdb) データベースを作成し、Jet データベース (.mdb) を圧縮して Jet レプリケーション管理を実行します。MDAC 2.7 は、最終リリースになります。JRO は 64 ビットの Windows オペレーティング システムで使用できません。JRO は、Microsoft Access 2007 ファイル形式でサポートされていません (* .accdb)。
* **16 ビット ODBC サポート:** 16 ビット アプリケーションを使用している場合は、32 ビット アプリケーションに移行する必要があります。 16 ビットの機能は非推奨し、64 ビット オペレーティング システムから削除しています。 詳細については、[サポート技術情報の記事 896458](https://support.microsoft.com/kb/896458) を参照してください。
* **単純な ole DB プロバイダー (MSDAOSP):** OLEDB の単純なプロバイダーは、単純なデータを OLE DB プロバイダーをすばやく構築するためのフレームワークを提供しています。 MSDAOSP が非推奨とされます。
* **ODBC カーソル ライブラリ:** ODBC カーソル ライブラリ (ODBCCR32.dll) が制限されたクライアント側データ カーソルを提供します。 ODBC カーソル ライブラリは非推奨とされました。アプリケーションは、代わりに、サーバー側カーソルの実装を使用できます。
* **プロセス外のインターフェイスのリモート処理を OLE DB:** OLEDB インターフェイスのリモート処理 (msdaps.dll) OLE DB プロバイダーがプロセス外で実行できるようにしようとしました。 OLEDB プロセス外のインターフェイスのリモート処理で非推奨とされます。
* **AppleTalk、Banyan Vines SQL ネットワーク ライブラリ:** Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet、および RPC SQL のネットワーク ライブラリが非推奨とされます。 これらのテクノロジのいずれかを使用する場合は、TCP/IP および名前付きパイプなど、他のネットワーク ライブラリのいずれかを使用するアプリケーションを変更する必要があります。

### <a name="mdacwdac-releases"></a>MDAC/WDAC リリース

以降で、最も早い、過去の MDAC/WDAC リリースのサポート シナリオの一覧を示します。

* **MDAC 1.5、MDAC 2.0、および MDAC 2.1:** MDAC のこれらのバージョンが Microsoft Windows NT のオプションの Pack、Microsoft Windows Platform SDK、または MDAC の Web サイトを介してリリースされた独立したリリースです。 MDAC のこれらのバージョンがサポートされていません。
* **MDAC 2.5:** MDAC のこのバージョンが、Windows 2000 オペレーティング システムに含まれています。 MDAC 2.5 のサービス パックが、対応する Windows 2000 service pack に含まれています。
* **MDAC 2.6:** MDAC 2.6 RTM、SP1、および SP2 はそれぞれ、SP1、および SP2、Microsoft SQL Server 2000 の RTM に含まれていた。 さらに、これらの MDAC サービス パックは、Microsoft SQL Server 2000 service pack のリリースのスケジュールに従って MDAC の Web サイトにリリースされました。 Windows 2000、Windows Millennium Edition、Windows NT、Windows 95、Windows 98 プラットフォームでは、このバージョンの MDAC とそのサービス パックをインストールできます。 このバージョンの MDAC はサポートされていません。
* **MDAC 2.7:** MDAC のこのバージョンは、Microsoft Windows XP RTM および SP1 オペレーティング システムに含まれています。 Windows 2000、Windows Millennium、Windows NT、および Windows 98 プラットフォームでは、このバージョンの MDAC とそのサービス パックをインストールできます。 このバージョンは、オペレーティング システムまたはそのサービス パックを通じてのみ、Windows XP のプラットフォームにインストールできます。 このバージョンの MDAC はサポートされていません。
* **MDAC 2.8:** MDAC のこのバージョンが Windows Server 2003 および Windows XP SP2 に付属しており、それ以降。 また、このバージョンの MDAC とそのサービス パックを Windows 2000 にインストールすることもできます。

  * MDAC 2.8 の 32 ビット バージョンもリリースされました MDAC の Web サイトに同時に Windows Server 2003 は、顧客にリリースされました。
  * MDAC 2.8 の 64 ビット バージョンは、Windows Server 2003 および Windows XP の 64 ビット版でリリースされました。

* **Windows Data Access Components (WDAC):** MDAC WDAC -"Windows Data Access Components"Windows Vista および Windows Server 2008 以降にその名前に変更します。 WDAC では、オペレーティング システムの一部として含まれてし、再頒布用に個別にご利用いただけません。 WDAC の保守性は、オペレーティング システムのライフ サイクルが適用されます。

  WDAC の 32 ビットおよび 64 ビットのバージョンについては、それぞれ、Windows オペレーティング システムの 32 ビットおよび 64 ビット バージョンでリリースします。

## <a name="obsolete-data-access-technologies"></a>古いデータ アクセス テクノロジ

旧式のテクノロジは、技術は、将来の製品のリリースから除外して、しない強化またはされたいくつかの製品リリースで更新します。 新しいアプリケーションを記述するときに、これらのテクノロジを使用しないでください。 これらのテクノロジを使用して記述されている既存のアプリケーションを変更するときに、ADO.NET などの現在のテクノロジへの移行を検討してください。

次のコンポーネントは古い形式と見なされます。

* **DB-Library:** DB ライブラリは、C Api を含む SQL Server に固有のプログラミング モデルです。 ない、Db-library の機能強化 SQL Server 6.5 以降。 SQL Server 2000 では、最終リリースの 64 ビット Windows オペレーティング システムに移植しません。
* **埋め込み SQL (SQL E):** E SQL では、SQL Server に固有のプログラミング モデルにより、Visual C のコードに埋め込まれる TRANSACT-SQL ステートメントをします。 機能が強化されてありません E SQL SQL Server 6.5 以降。 SQL Server 2000 では、最終リリースの 64 ビット Windows オペレーティング システムに移植しません。
* **データ アクセス オブジェクト (DAO):** DAO JET (アクセス) データベースへのアクセスを提供します。 この API は、Microsoft Visual Basic、Microsoft Visual C、およびスクリプト言語から使用できます。 Microsoft Office 2000 および Office XP には含まれています。 DAO 3.6 は、このテクノロジの最終バージョンです。 これは、64 ビット Windows オペレーティング システムで使用できるされません。
* **リモート データ オブジェクト (RDO):** RDO が具体的には、リモート ODBC リレーショナル データ ソースにアクセスするように設計および ODBC を使用して、複雑なアプリケーションのコードを使用せずに容易になりました。 Microsoft Visual Basic バージョン 4、5、および 6 には含まれています。 RDO バージョン 2.0 は、このテクノロジの最終バージョンでした。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
