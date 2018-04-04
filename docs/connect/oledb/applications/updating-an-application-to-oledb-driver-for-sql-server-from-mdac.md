---
title: MDAC から SQL Server の OLE DB ドライバーへのアプリケーションの更新 |Microsoft ドキュメント
description: MDAC から SQL Server の OLE DB Driver をアプリケーションの更新
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, vs. MDAC
- OLE DB Driver for SQL Server, vs. MDAC
- data access [OLE DB Driver for SQL Server], vs. MDAC
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b0581e1423cd2731b1edb0dbdc0f26523f445a7
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="updating-an-application-to-ole-db-driver-for-sql-server-from-mdac"></a>MDAC から SQL Server の OLE DB ドライバーへのアプリケーションの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  さまざまな OLE DB Driver for SQL Server と Microsoft Data Access Components (MDAC); の違いがあります。Windows Vista 以降、Windows Data Access Components (Windows DAC) に、データ アクセス コンポーネントが呼び出さようになりました。 ネイティブ データ アクセスを提供します両方[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベースの場合は、SQL Server は、の新機能を公開に特に設計されていますの OLE DB Driver[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中では、以前のバージョンとの下位互換性を維持しながら、します。   

 さらに、MDAC には、OLE DB、ODBC、および ActiveX データ オブジェクト (ADO) を使用するためのコンポーネントが含まれている、OLE DB Driver for SQL Server しか実装されていない OLE DB (ただし、ADO は、SQL Server の OLE DB ドライバーの機能にアクセスできます)。  

 OLE DB Driver for SQL Server および MDAC は、次の領域で異なります。  

-   ADO を使用して、SQL Server の OLE DB ドライバーにアクセスするユーザーには、SQL OLE DB プロバイダーにアクセスする場合よりもフィルター処理機能が少ないことがあります。  

-   ADO アプリケーションで SQL Server の OLE DB Driver を使用して、計算列を更新しようとすると、エラーが報告されます。 MDAC では、更新が受け付けられたうえで、無視されていました。  

-   OLE DB Driver for SQL Server は、自己完結型の単一のダイナミック リンク ライブラリ (DLL) ファイルです。 配布を容易にすることと、セキュリティの危険にさらされるのを防ぐことの両面から、最小限のインターフェイスしか公開されません。  

-   OLE DB インターフェイスだけがサポートされます。  

-   OLE DB Driver for SQL Server の名前は、MDAC で使用するものと異なります。  

-   MDAC コンポーネントによって提供されるユーザーがアクセスできる機能は、SQL Server の OLE DB Driver を使用するときに使用できます。 この機能には、接続プーリング、ADO サポート、クライアント カーソルのサポートなどがあります。 これらの機能を使用する場合、OLE DB Driver for SQL Server は、データベースとの接続のみを提供します。 MDAC は、トレース、管理制御、およびパフォーマンス カウンターなどの機能を提供します。  

-   アプリケーションは、SQL Server の OLE DB ドライバーと OLE DB core services を使用することができますが、OLE DB カーソル エンジンを使用する場合、オプションを使用して、データ型互換性カーソル エンジンは、新しいの知識があるないために生じる可能性のある潜在的な問題を回避します。[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]データ型。  

-   OLE DB Driver for SQL Server が前へのアクセスをサポートしている[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  

-   OLE DB Driver for SQL Server では、XML との統合は含まれません。 OLE DB Driver for SQL Server では、選択をサポートしています. XML のクエリが、その他の XML 機能をサポートしていません。 ただしは、OLE DB Driver for SQL Server のサポート、 **xml**データ型がで導入された[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。  

-   OLE DB Driver for SQL Server では、接続文字列の属性のみを使用してクライアント側のネットワーク ライブラリの構成をサポートします。 ネットワーク ライブラリをさらに詳細に構成する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーを使用する必要があります。  

-   OLE DB Driver for SQL Server は、odbcbcp.dll と互換性がありません。 SQL Server の OLE DB Driver を使用するために msoledbsql.lib とリンクするには、アプリケーションをリビルドしてください。    

-   MDAC 接続文字列、ブール値を許可する (**true**) の**Trusted_Connection**キーワード。 OLE DB Driver for SQL Server 接続文字列を使用する必要があります**はい**または**ありません**です。  

-   警告とエラーが一部変更されています。 警告およびこれで、サーバーにより返されたエラーは、重大度は、SQL Server の OLE DB ドライバーに渡される場合を保持します。 特定の警告やエラーのトラッピングに依存しているアプリケーションは、十分にテストする必要があります。  

-   OLE DB Driver for SQL Server より厳密なエラーが OLE DB 仕様に厳密に準拠していない一部のアプリケーションの動作が異なりますをつまり MDAC よりもチェックします。 たとえば、SQLOLEDB プロバイダーがパラメーター名の先頭は、ルールを実行しなかった ' @' 結果パラメーターが SQL Server の OLE DB Driver はします。  

-   OLE DB Driver for SQL Server の動作が異なる MDAC から接続が失敗しました。 たとえば、OLE DB Driver for SQL Server では、エラーを報告、呼び出し元アプリケーションに対し、MDAC は、障害が発生した接続のキャッシュされたプロパティ値を返します。  

-   OLE DB Driver for SQL Server では、Visual Studio Analyzer イベントを生成しませんが、代わりに Windows トレース イベントを生成します。  

-   パフォーマンス モニターでは、OLE DB Driver for SQL Server を使用できません。 パフォーマンス モニターは、Windows に付属している MDAC SQLODBC ドライバーを使用する DSN のみと併用できる Windows ツールです。  

-   OLE DB Driver for SQL Server に接続されている[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]以降のバージョンでサーバー エラー 16947 が SQL_ERROR として返されるとします。 このエラーは、位置指定更新または位置指定削除による行の更新や削除が失敗したときに発生します。 任意のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続している MDAC では、サーバー エラー 16947 は警告 (SQL_SUCCESS_WITH_INFO) として返されます。  

-   OLE DB Driver for SQL Server の実装、 **IDBDataSourceAdmin**インターフェイスでしたが、以前は実装されているオプションの OLE DB インターフェイスが、 **CreateDataSource**これのメソッド省略可能なインターフェイスを実装します。 [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

-   SQL Server の OLE DB Driver シノニムを返しますのテーブルと TABLE_INFO スキーマ行セット、TABLE_TYPE を SYNONYM に設定します。  

-   データ型の値を返す**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、 **udt**、クライアントのバージョンにその他のラージ オブジェクト型を返すことはできませんまたはよりも前[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 戻り値としてこれらの型を使用する場合は、SQL Server の OLE DB Driver を使用する必要があります。  

-   手動および暗黙のトランザクションの開始時に実行される次のステートメントにより、MDAC が OLE DB Driver for SQL Server は使用できません。 これらは、自動コミット モードで実行する必要があります。  

    -   すべてのフルテキスト操作 (インデックスおよびカタログ DDL)  

    -   すべてのデータベース操作 (データベースの作成、変更、および削除)  

    -   再構成時  

    -   Shutdown  

    -   Kill  

    -   バックアップ  

-   MDAC アプリケーションから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続すると、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたデータ型は、次の表に示すような、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] と互換性を持つデータ型として扱われます。  

    |SQL Server 2005 の型|SQL Server 2000 の種類|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  

     この型マッピングは、列のメタデータに返される値に影響を与えます。 たとえば、**テキスト**列の最大サイズは 2,147, 483,647 が、OLE DB Driver for SQL Server の最大サイズを報告する**varchar (max)** 2,147, 483,647 または-1 プラットフォームとしての列です。  

-   OLE DB Driver for SQL Server 接続文字列内のあいまいさを許可 (たとえば、いくつかのキーワードを複数回指定することがあり、位置 or の優先順位に基づいた解決と競合するキーワードを許可することがあります) の旧バージョンと互換性の理由からです。 OLE DB Driver for SQL Server の今後のリリースは、接続文字列のあいまいさを許可しない場合があります。 接続文字列のあいまいさの依存を排除する OLE DB Driver for SQL Server を使用するアプリケーションを変更する場合は、ことをお勧めを勧めします。  

-   OLE DB Driver for SQL Server および MDAC; 間の動作に違いがあるトランザクションを開始する OLE DB の呼び出しを使用する場合トランザクションがすぐに開始 OLE DB Driver for SQL Server が、MDAC を使用して最初のデータベースにアクセスした後にトランザクションが開始されます。 ストアド プロシージャとバッチの動作に影響するためできますこの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]@ 必要があります@TRANCOUNTバッチまたはストアド プロシージャが終了すると、バッチやストアド プロシージャの開始時と同じであります。  

-   OLE DB Driver for SQL Server で ITransactionLocal::BeginTransaction に即座に開始するトランザクションが発生します。 MDAC では、暗黙のトランザクション モードを必要とするステートメントをアプリケーションが実行するまで、トランザクションの開始が遅延されました。 詳細については、「[SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md)」を参照してください。  


 両方 OLE DB Driver for SQL Server と MDAC のサポートは read committed トランザクション分離の行のバージョン管理が OLE DB ドライバーのみを使用して、SQL Server サポート スナップショット トランザクション分離のためです。 (プログラミング用語では、「行のバージョン管理機能を使用した Read Committed トランザクション分離」は「Read Committed トランザクション」と同義語です)。  

## <a name="see-also"></a>参照  
 [SQL Server の OLE DB ドライバーとアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
