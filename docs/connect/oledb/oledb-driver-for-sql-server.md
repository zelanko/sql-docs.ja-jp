---
title: OLE DB Driver for SQL Server |Microsoft ドキュメント
description: OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: OLE DB Driver
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server
- MSOLEDBSQL
- native data access [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 30ca6b7e894482aa2a94c778cc44bfcbba2a759e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server は、スタンドアロンのデータ アクセス アプリケーション プログラミング インターフェイス (API)、OLE DB で導入されたため[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 OLE DB Driver for SQL Server では、1 つのダイナミック リンク ライブラリ (DLL) で、SQL OLE DB ドライバーを提供します。 また、Windows Data Access Components (Windows DAC、以前の Microsoft Data Access Components (MDAC)) にはない新しい機能も用意されています。 OLE DB Driver for SQL Server は、新しいアプリケーションを作成したり、既存のアプリケーションで導入された機能を活用する必要がある拡張を使用できます[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、複数のアクティブな結果セット (MARS)、ユーザー定義データ型 (UDT)、クエリなど通知、スナップショット分離、および XML データ型をサポートします。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server と Windows DAC、および SQL Server の OLE DB ドライバーを Windows DAC アプリケーションを更新する前に考慮すべき問題に関する情報の相違点の一覧は、次を参照してください[sql OLE DB Driver をアプリケーションの更新。MDAC からサーバー](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)です。  
  
 SQL Server の OLE DB Driver は、OLE DB Core Services Windows DAC 付属と組み合わせて使用できますが、これは要件ではありません。コア サービスを使用するかどうかを選択は、個々 のアプリケーション (たとえば、接続プールが必要な場合) の要件によって異なります。  
  
 ActiveX データ オブジェクト (ADO) アプリケーションは、SQL Server の OLE DB Driver を使用する可能性がありますが、と共に ADO を使用することをお勧め、 **DataTypeCompatibility**接続文字列キーワード (またはそれに対応する**DataSource**プロパティ)。 ADO アプリケーションで導入されたこれらの新機能を悪用 OLE DB Driver for SQL Server を使用する場合[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]接続文字列キーワードまたは OLE DB プロパティを使用して、OLE DB Driver for SQL Server を使用して利用可能なまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 ADO で新機能の使用に関する詳細については、次を参照してください。 [ADO を使用して OLE DB Driver for SQL Server と](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)です。  
  
 OLE DB Driver for SQL Server は、OLE DB を使用して SQL server のネイティブ データ アクセスの簡略化されたメソッドを提供するよう設計されました。 導入および Microsoft Windows プラットフォームの一部になっている現在の Windows DAC コンポーネントを変更することがなくデータ アクセスの新機能を展開する方法を提供します。  
  
 OLE DB Driver for SQL Server での Windows DAC コンポーネントを使用中には明示的に特定のバージョンの Windows DAC に依存 SQL Server の OLE DB ドライバーでサポートされる任意のオペレーティング システムと共にインストールされている Windows DAC のバージョンと SQL Server の OLE DB Driver を使用できます。  

 ## <a name="different-generations-of-ole-db-drivers"></a>OLE DB ドライバーのさまざまな世代

SQL Server の Microsoft OLE DB プロバイダーの 3 つの個別の世代があります。

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1.Microsoft OLE DB Provider for SQL Server (SQLOLEDB)
[Microsoft OLE DB Provider for SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) がまだの一部として出荷[Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx)です。 もはやに維持されませんし、このドライバーを使用して、新規の開発をお勧めできません。

### <a name="2-sql-server-native-client-snac"></a>2.SQL Server Native Client (SNAC)
以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[は、SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md)に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれています[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を通じて[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。

[2011年で非推奨と発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)し、このドライバーを使用して、新規の開発をお勧めできません。 SNAC ライフ サイクル、および利用可能なダウンロードの詳細についてを参照してください[説明 SNAC ライフ サイクル](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)です。

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3.Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)
OLE DB が[undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) 2018年でリリースされたとします。

新しい OLE DB プロバイダーが呼び出されます Microsoft OLE DB ドライバーの SQL Server (MSOLEDBSQL)。 新しいプロバイダーは、今後、最新のサーバー機能と更新されます。

> [!NOTE]
> SQL Server の新しい Microsoft OLE DB Driver を使用して、既存のアプリケーションには、SQLOLEDB または SQLNCLI, から MSOLEDBSQL に、接続文字列を変換する計画してください。
  
## <a name="in-this-section"></a>このセクションの内容  
[OLE DB Driver for SQL Server をいつ使用するか](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 OLE DB Driver for SQL Server が適合するしくみで Microsoft データ アクセス テクノロジについて説明します。 どのように Windows DAC および ADO.NET と比較し、データ アクセス テクノロジを使用するかを決めるのポインターを提供します。  
  
 [OLE DB Driver for SQL Server の機能](../oledb/features/oledb-driver-for-sql-server-features.md )  
 SQL Server の OLE DB ドライバーでサポートされる機能をについて説明します。  
  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 SQL Server の開発では、Windows DAC を使用するコンポーネントとは異なる方法、およびそれに ADO を使用する方法を含む OLE DB ドライバーの概要を示します。  
  
 このセクションでは、SQL Server のインストールと展開、SQL Server ライブラリの OLE DB ドライバーの再配布する方法を含む OLE DB Driver も説明します。  
  
 [OLE DB Driver for SQL Server のシステム要件](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 SQL Server の OLE DB Driver を使用するために必要なシステム リソースについて説明します。  
  
 [OLE DB Driver for SQL Server のプログラミング](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 SQL Server の OLE DB Driver を使用する方法についてを説明します。  
  
 [OLE DB Driver for SQL Server の詳細情報の検索](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 外部リソースへのリンクを含むと参考資料ではさらに、SQL Server 用の OLE DB ドライバーに関する追加リソースを提供します。  
  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 Native Client からのアプリケーションの更新](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [OLE DB の操作方法に関するトピック](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
