---
title: Microsoft OLE DB Driver for SQL Server | Microsoft Docs
description: Microsoft OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 6fd7f5262359597694717927c0a87f4861cc6b4f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108054"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server は、スタンドアロンのデータ アクセス アプリケーション プログラミング インターフェイス (API)、OLE DB で導入されたため[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。 OLE DB Driver for SQL Server では、1 つのダイナミック リンク ライブラリ (DLL) で、SQL OLE DB ドライバーを提供します。 また、Windows Data Access Components (Windows DAC、以前の Microsoft Data Access Components (MDAC)) にはない新しい機能も用意されています。 MARS (複数のアクティブな結果セット)、UDT (ユーザー定義データ型)、クエリ通知、スナップショット分離、XML データ型のサポートなどの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入された機能を必要とする新しいアプリケーションを作成したり、これらの機能で既存のアプリケーションを強化するために、OLE DB Driver for SQL Server を使用できます。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server と Windows DAC、および SQL Server 用の OLE DB ドライバーを Windows DAC アプリケーションの更新前に考慮すべき問題に関する情報の相違点の一覧は、次を参照してください[sql OLE DB ドライバーへのアプリケーションの更新。MDAC からサーバー](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)します。  
  
 また、OLE DB Driver for SQL Server は、Windows DAC 付属の OLE DB Core Services と共に使用できますが、必須ではありません。OLE DB Core Services を使用するかどうかは、個々のアプリケーションの要件 (たとえば、接続プールが必要であるかどうかなど) によって異なります。  
  
 ActiveX データ オブジェクト (ADO) アプリケーションは、SQL Server の OLE DB Driver を使用する可能性がありますと組み合わせて、ADO を使用することをお勧め、 **DataTypeCompatibility**接続文字列キーワード (またはそれに対応する**DataSource**プロパティ)。 ADO アプリケーションで導入された新機能を悪用 OLE DB Driver for SQL Server を使用する場合[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、OLE DB Driver for SQL Server を使用して接続文字列キーワードまたは OLE DB プロパティを介して提供されるまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 ADO を使用したこれらの機能の使用に関する詳細については、次を参照してください。 [OLE DB Driver for SQL Server で使用する ADO](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)します。  
  
 OLE DB Driver for SQL Server は、OLE DB を使用して簡単に SQL Server へのネイティブ データ アクセスを実現できるように設計されています。 導入および Microsoft Windows プラットフォームの一部になっている現在の Windows DAC コンポーネントを変更することがなくデータ アクセスの新機能を展開する方法を提供します。  
  
 OLE DB Driver for SQL Server では Windows DAC のコンポーネントを使用しますが、明確に特定バージョンの Windows DAC に依存しているわけではありません。 SQL Server の OLE DB ドライバーでサポートされる任意のオペレーティング システムと共にインストールされる Windows DAC のバージョンで SQL Server の OLE DB Driver を使用できます。  

 ## <a name="different-generations-of-ole-db-drivers"></a>OLE DB ドライバーのさまざまな世代

SQL Server の Microsoft OLE DB プロバイダーの 3 つの個別の世代があります。

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1.Microsoft OLE DB Provider for SQL Server (SQLOLEDB)
[Microsoft OLE DB Provider for SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)の一部としても付属しています (SQLOLEDB) [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx)します。 もはやそれは維持されませんし、このドライバーを使用して、新規の開発をお勧めできません。

### <a name="2-sql-server-native-client-snac"></a>2.SQL Server Native Client (SNAC)
以降では[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [SQL サーバー ・ Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md)に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を通じて[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]します。

[2011年で非推奨と発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)し、このドライバーを使用して、新規の開発をお勧めできません。 SNAC ライフ サイクルと利用可能なダウンロードの詳細についてを参照してください[SNAC ライフ サイクルを説明した](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)します。

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3.Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)
OLE DB が[取り消す](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)2018 年にリリースされたとします。

新しい OLE DB プロバイダーと呼ばれる Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)。 今後、最新のサーバー機能では、新しいプロバイダーが更新されます。

> [!NOTE]
> 既存のアプリケーションを SQL Server の新しい Microsoft OLE DB Driver を使用するには、MSOLEDBSQL SQLOLEDB または SQLNCLI, から、接続文字列に変換する計画する必要があります。
  
## <a name="in-this-section"></a>このセクションの内容  
[OLE DB Driver for SQL Server をいつ使用するか](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 マイクロソフトのデータ アクセス テクノロジにおける OLE DB Driver for SQL Server の位置付け、Windows DAC および ADO.NET との比較、使用するデータ アクセス テクノロジの決定方法について説明します。  
  
 [OLE DB Driver for SQL Server の機能](../oledb/features/oledb-driver-for-sql-server-features.md )  
 SQL Server の OLE DB ドライバーによってサポートされる機能をについて説明します。  
  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 OLE DB Driver for SQL Server の開発における、Windows DAC との違い、使用されるコンポーネント、ADO と併用する方法などの概要を示します。  
  
 このセクションでは、SQL Server のインストールと展開、SQL Server ライブラリの OLE DB ドライバーの再配布する方法などの OLE DB ドライバーも説明します。  
  
 [OLE DB Driver for SQL Server のシステム要件](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 OLE DB Driver for SQL Server を使用して、必要なシステム リソースについて説明します。  
  
 [OLE DB Driver for SQL Server のプログラミング](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 SQL Server 用の OLE DB ドライバーの使用方法についてを説明します。  
  
 [OLE DB Driver for SQL Server の詳細情報の検索](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 SQL server の外部リソースへのリンクなど、詳しい補助資料には、OLE DB ドライバーに関する追加リソースを提供します。  
  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 Native Client からのアプリケーションの更新](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [OLE DB の使用法に関するトピック](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
