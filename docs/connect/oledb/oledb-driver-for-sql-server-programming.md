---
title: SQL Server プログラミング用の OLE DB ドライバー |Microsoft ドキュメント
description: OLE DB ドライバーの SQL Server プログラミング
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
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
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fe6342e3a61ecc59594917431c026681e51f8e63
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-driver-for-sql-server-programming"></a>SQL Server プログラミング用の OLE DB ドライバー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server は、スタンドアロンのデータ アクセス アプリケーション プログラミング インターフェイス (API)、OLE DB で導入されたため[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 OLE DB Driver for SQL Server では、1 つのダイナミック リンク ライブラリ (DLL) で、SQL OLE DB ドライバーを提供します。 また、Windows Data Access Components (Windows DAC、以前の Microsoft Data Access Components (MDAC)) にはない新しい機能も用意されています。 OLE DB Driver for SQL Server は、新しいアプリケーションを作成したり、既存のアプリケーションで導入された機能を活用する必要がある拡張を使用できます[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、複数のアクティブな結果セット (MARS)、ユーザー定義データ型 (UDT)、クエリなど通知、スナップショット分離、および XML データ型をサポートします。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server と Windows DAC、および SQL Server の OLE DB ドライバーを Windows DAC アプリケーションを更新する前に考慮すべき問題に関する情報の相違点の一覧は、次を参照してください[sql OLE DB Driver をアプリケーションの更新。MDAC からサーバー](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)です。  
  
 SQL Server の OLE DB Driver は、OLE DB Core Services Windows DAC 付属と組み合わせて使用できますが、これは要件ではありません。コア サービスを使用するかどうかを選択は、個々 のアプリケーション (たとえば、接続プールが必要な場合) の要件によって異なります。  
  
 ActiveX データ オブジェクト (ADO) アプリケーションは、SQL Server の OLE DB Driver を使用する可能性がありますが、と共に ADO を使用することをお勧め、 **DataTypeCompatibility**接続文字列キーワード (またはそれに対応する**DataSource**プロパティ)。 ADO アプリケーションで導入されたこれらの新機能を悪用 OLE DB Driver for SQL Server を使用する場合[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]接続文字列キーワードまたは OLE DB プロパティを使用して、OLE DB Driver for SQL Server を使用して利用可能なまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 ADO で新機能の使用に関する詳細については、次を参照してください。 [ADO を使用して OLE DB Driver for SQL Server と](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)です。  
  
 OLE DB Driver for SQL Server は、OLE DB を使用して SQL server のネイティブ データ アクセスの簡略化されたメソッドを提供するよう設計されました。 導入および Microsoft Windows プラットフォームの一部になっている現在の Windows DAC コンポーネントを変更することがなくデータ アクセスの新機能を展開する方法を提供します。  
  
 OLE DB Driver for SQL Server での Windows DAC コンポーネントを使用中には明示的に特定のバージョンの Windows DAC に依存 SQL Server の OLE DB ドライバーでサポートされる任意のオペレーティング システムと共にインストールされている Windows DAC のバージョンと SQL Server の OLE DB Driver を使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)  
 大幅な新しい OLE DB Driver for SQL Server の機能を一覧表示します。  
  
 [OLE DB Driver for SQL Server をいつ使用するか](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 OLE DB Driver for SQL Server が適合するしくみで Microsoft データ アクセス テクノロジについて説明します。 どのように Windows DAC および ADO.NET と比較し、データ アクセス テクノロジを使用するかを決めるのポインターを提供します。  
  
 [OLE DB Driver for SQL Server の機能](../oledb/features/oledb-driver-for-sql-server-features.md )  
 SQL Server の OLE DB ドライバーでサポートされる機能をについて説明します。  
  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 SQL Server の開発では、Windows DAC を使用するコンポーネントとは異なる方法、およびそれに ADO を使用する方法を含む OLE DB ドライバーの概要を示します。  
  
 このセクションでは、SQL Server のインストールと展開、SQL Server ライブラリの OLE DB ドライバーの再配布する方法を含む OLE DB Driver も説明します。  
  
 [OLE DB Driver for SQL Server のシステム要件](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 SQL Server の OLE DB Driver を使用するために必要なシステム リソースについて説明します。  
  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
 SQL Server の OLE DB Driver を使用する方法についてを説明します。  
  
 [OLE DB Driver for SQL Server の詳細情報の検索](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 外部リソースへのリンクを含むと参考資料ではさらに、SQL Server 用の OLE DB ドライバーに関する追加リソースを提供します。  
  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 Native Client からのアプリケーションの更新](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [OLE DB の操作方法に関するトピック](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
