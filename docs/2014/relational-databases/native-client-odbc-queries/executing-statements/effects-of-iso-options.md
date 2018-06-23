---
title: ISO オプションの効果 |Microsoft ドキュメント
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
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: faea519caeac29c42c35c7aabc4931d08b8e4224
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075508"
---
# <a name="effects-of-iso-options"></a>ISO オプションの効果
  ODBC 標準は、ISO 標準と密接に対応しています。ODBC アプリケーションは、ODBC ドライバーの動作が標準に準拠していることを前提としています。 ODBC 標準で定義するとより密接に適合してその動作をする、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは常に、接続先の SQL Server のバージョンで利用可能な ISO オプションを使用します。  
  
 ときに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでのインスタンスに接続[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、クライアントを使用しているサーバーを検出、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーとのいくつかのオプションを設定します。  
  
 ステートメント自体はドライバーが実行します。ODBC アプリケーションはステートメントの実行に対して何の要求も行いません。 ISO オプションを設定することで、SQL Native Client ODBC ドライバーを使用する ODBC アプリケーションの移植性が高まります。これは、サーバーの動作が ISO 標準に準拠するためです。  
  
 DB-Library ベースのアプリケーションは、通常これらのオプションを有効にしません。 違いが見られるサイトに問題を同じ SQL ステートメントを実行している必要がありますいないいることを仮定するときに、ODBC または Db-library クライアント間の動作が指す、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。 最初に再実行してください同じ SET オプションと Db-library 環境で、ステートメントによって使用されているよう、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。  
  
 SET オプションはユーザーやアプリケーションがいつでも有効または無効にできるので、ストアド プロシージャやトリガーの開発者は、上記の SET オプションを有効にした場合と無効にした場合の両方で、開発したプロシージャやトリガーをテストする必要があります。 これにより、プロシージャやトリガーの起動時に、接続に設定されているオプションに関係なく、プロシージャやトリガーが適切に動作することを確認できます。 これらのオプションのいずれかについて特定の設定が必要なトリガーやストアド プロシージャは、そのトリガーやストアド プロシージャの起動時に SET ステートメントを実行する必要があります。 この SET ステートメントは、トリガーやストアド プロシージャが実行されている間だけ有効になり、トリガーやストアド プロシージャが終了すると元の設定が復元されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続しているときは、4 番目の SET オプションの CONCAT_NULL_YIELDS_NULL も有効になります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは場合にこれらのオプションを設定していない AnsiNPW = NO データ ソース、またはいずれかで指定されます[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)または[SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)です。  
  
 既に述べたとおり、ISO オプションと同様に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに場合に、QUOTED_IDENTIFIER オプションがオンにならない QuotedID = NO データ ソース、またはいずれかで指定されます**SQLDriverConnect**または**SQLBrowseConnect**です。  
  
 ドライバーが SET オプションの現在の状態を確認できるようにするために、ODBC アプリケーションでは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] SET ステートメントを使用して SET オプションを設定しないようにします。 これらのオプションを設定する場合は、データ ソースまたは接続オプションのみを使用するようにします。 アプリケーションが SET ステートメントを実行した場合、ドライバーは不正な SQL ステートメントを生成する可能性があります。  
  
## <a name="see-also"></a>参照  
 [ステートメントを実行する&#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  