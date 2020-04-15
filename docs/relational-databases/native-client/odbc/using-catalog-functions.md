---
title: カタログ関数の使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 961e44e22ba7db89537f4505a8dec401f9fd69b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303633"
---
# <a name="using-catalog-functions"></a>カタログ関数の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  どのようなデータベースであっても、その構造は、データベースに格納されたデータを保持するような構造になっています。 この構造の定義は、権限などその他の情報と共にカタログに保存されます。カタログは、システム テーブルのセットとして実装され、データ辞書と呼ばれることもあります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーを使用すると、アプリケーションは ODBC カタログ関数の呼び出しを通じてデータベース構造を決定できます。 カタログ関数は情報を結果セットとして返す関数で、カタログのシステム テーブルをクエリするカタログ ストアド プロシージャを使用して実装されます。 たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。 この場合、標準の ODBC カタログ関数を使用して、アプリケーションが接続している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からカタログ情報を取得します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は分散クエリをサポートします。分散クエリは、1 つのクエリで複数の異種 OLE DB データ ソースのデータにアクセスするクエリです。 リモートの OLE DB データ ソースへアクセスするための方法として、目的のデータ ソースをリンク サーバーとして定義する方法があります。 これは、 [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)を使用して行うことができます。 リンク サーバーを定義すると、このサーバーのオブジェクトを次のような 4 部構成の名前を使用して Transact-SQL ステートメントで参照できるようになります。  
  
 *linked_server_name.カタログ.スキーマ.object_name*.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバーからのカタログ情報の取得に役立つ、次の 2 つのドライバー固有の関数をサポートします。  
  
-   **SQLLinkedServers**  
  
     ローカル サーバーに対して定義されているリンク サーバーの一覧を返します。  
  
-   **SQLLinkedCatalogs**  
  
     リンク サーバーに含まれるカタログの一覧を返します。  
  
 リンク サーバー名とカタログ名を取得した後、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバは _、2_つの部分から構成される名前の linked_server_name を使用してカタログから情報を取得できます **。**_次_の ODBC カタログ関数の*カタログ名*のカタログ:  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 2部構成の_linked_server_name_**.**_カタログ_は[、SQL 外向キー](../../../relational-databases/native-client-odbc-api/sqlforeignkeys.md)の*FK カタログ名*と*PK カタログ名*でもサポートされています。  
  
 SQLLinkedServers と SQLLinkedCatalogs を使用する場合は、次のファイルが必要です。  
  
-   sqlncli.h  
  
     リンク サーバーのカタログ関数の関数プロトタイプと定数定義を含むファイルです。 sqlncli.h を ODBC アプリケーションにインクルードし、アプリケーションのコンパイル時にはこのファイルをインクルード パスに配置しておく必要があります。  
  
-   sqlncli11.lib  
  
     リンカーのライブラリ パスに存在し、リンクされるファイルとして指定する必要があります。 sqlncli11.lib は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。  
  
-   sqlncli11.dll  
  
     実行時に存在する必要があります。 sqlncli11.dll は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;SQL Server ネイティブ クライアント](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [特権](../../../relational-databases/native-client-odbc-api/sqlcolumnprivileges.md)   
 [SQL カラム](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)   
 [プライマリキー](../../../relational-databases/native-client-odbc-api/sqlprimarykeys.md)   
 [SQL テーブル特典](../../../relational-databases/native-client-odbc-api/sqltableprivileges.md)   
 [SQL テーブル](../../../relational-databases/native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../../relational-databases/native-client-odbc-api/sqlstatistics.md)  
  
  
