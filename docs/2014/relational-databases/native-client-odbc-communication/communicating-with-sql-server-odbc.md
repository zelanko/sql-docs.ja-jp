---
title: SQL Server との通信 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021199"
---
# <a name="communicating-with-sql-server-odbc"></a>SQL Server との通信 (ODBC)
  ODBC アプリケーションがのインスタンスと通信するには [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、環境ハンドルと接続ハンドルを割り当て、データソースに接続する必要があります。 接続が確立されると、アプリケーションからサーバーにクエリを送信し、任意の結果セットを処理できます。 データ ソースの使用が終了したら、アプリケーションでデータ ソースを切断して接続ハンドルを解放します。 すべての接続ハンドルを解放してから、環境ハンドルを解放します。  
  
 アプリケーションからは任意の数のデータ ソースに接続できます。 また、アプリケーションでは、複数のドライバーと複数のデータ ソースの組み合わせ、1 つのドライバーと複数データ ソースの組み合わせ、1 つのドライバーと 1 つのデータ ソースへの複数の接続を使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC サンプルは、MSDN の[SQL Server ダウンロード](https://go.microsoft.com/fwlink/?LinkId=62796)ページからダウンロードできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [環境ハンドルの割り当て](allocating-an-environment-handle.md)  
  
-   [接続ハンドルの割り当て](allocating-a-connection-handle.md)  
  
-   [SQL Server Native Client ODBC データ ソース](../../integration-services/connection-manager/data-sources.md)  
  
-   [ODBC&#41;&#40;データソースへの接続](connecting-to-a-data-source-odbc.md)  
  
-   [データ ソースからの切断](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
