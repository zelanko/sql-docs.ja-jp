---
title: SQL Server Native Client ODBC データ ソース |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b74f989db617c2fcd86e0d823b9bb563c7dcda1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075027"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC データ ソース
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソース名 (DSN) によって ODBC データ ソースが特定されます。ODBC データ ソースには、特定のサーバー上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続するために ODBC アプリケーションで必要となるすべての情報が含まれています。 ODBC データ ソース名を定義するには次の 2 つの方法があります。  
  
-   クライアント コンピューターで コントロール パネルの 管理ツールを開きをダブルクリックして**データ ソース (ODBC)** です。 ODBC データ ソース アドミニストレーターが起動します。これを使用して DSN を作成できます。  
  
-   ODBC アプリケーションで呼び出す[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソースには次の情報が含まれます。  
  
-   データ ソースの名前です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスとの接続に必要な情報。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスで使用する既定のデータベース (省略可)。  
  
-   使用する ANSI オプション、パフォーマンス統計情報をログに記録するかどうかなどの設定 (省略可)。  
  
 データ ソース経由で接続する場合、ODBC アプリケーションは必要ありません。 ただしアプリケーションでは、ドライバーが DSN から検出する接続情報と同じ情報を、ODBC 接続関数に対して指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server との通信&#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  