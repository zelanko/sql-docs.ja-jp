---
title: SQL Server Native Client ODBC データ ソース |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4553908f106528ce87dfdea268e0257959551da4
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702513"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC データ ソース
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソース名 (DSN) によって ODBC データ ソースが特定されます。ODBC データ ソースには、特定のサーバー上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続するために ODBC アプリケーションで必要となるすべての情報が含まれています。 ODBC データ ソース名を定義するには次の 2 つの方法があります。  
  
-   クライアント コンピューターで コントロール パネルの 管理ツールを開きをダブルクリックして**データ ソース (ODBC)** です。 ODBC データ ソース アドミニストレーターが起動します。これを使用して DSN を作成できます。  
  
-   ODBC アプリケーションで呼び出す[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソースには次の情報が含まれます。  
  
-   データ ソースの名前です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスとの接続に必要な情報。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスで使用する既定のデータベース (省略可)。  
  
-   使用する ANSI オプション、パフォーマンス統計情報をログに記録するかどうかなどの設定 (省略可)。  
  
 データ ソース経由で接続する場合、ODBC アプリケーションは必要ありません。 ただしアプリケーションでは、ドライバーが DSN から検出する接続情報と同じ情報を、ODBC 接続関数に対して指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server との通信&#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
