---
title: SQL Server (ODBC) との通信 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92e261d2c1cb1c96d3cce7cbb2ba13dcb0bad60c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134207"
---
# <a name="communicating-with-sql-server-odbc"></a>SQL Server との通信 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC アプリケーションのインスタンスと通信する[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]環境を割り当てる必要があります、および接続を処理し、データ ソースに接続します。 接続が確立されると、アプリケーションからサーバーにクエリを送信し、任意の結果セットを処理できます。 データ ソースの使用が終了したら、アプリケーションでデータ ソースを切断して接続ハンドルを解放します。 すべての接続ハンドルを解放してから、環境ハンドルを解放します。  
  
 アプリケーションからは任意の数のデータ ソースに接続できます。 また、アプリケーションでは、複数のドライバーと複数のデータ ソースの組み合わせ、1 つのドライバーと複数データ ソースの組み合わせ、1 つのドライバーと 1 つのデータ ソースへの複数の接続を使用できます。  
  
 ダウンロードすることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC のサンプル コードから、 [SQL Server ダウンロード](https://go.microsoft.com/fwlink/?LinkId=62796)MSDN ページにアクセスします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [環境ハンドルの割り当て](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [接続ハンドルの割り当て](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC データ ソース](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [データ ソースに接続する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [データ ソースからの切断](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
