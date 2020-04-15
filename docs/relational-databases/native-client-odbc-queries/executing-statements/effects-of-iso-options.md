---
title: ISO オプションの効果 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: adf37d03f5ea4f06be4d58e60deca68e10d45abb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297938"
---
# <a name="effects-of-iso-options"></a>ISO オプションの効果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC 標準は、ISO 標準と密接に対応しています。ODBC アプリケーションは、ODBC ドライバーの動作が標準に準拠していることを前提としています。 ODBC 標準で定義されている動作をより厳密に準拠させるために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは常に接続する SQL Server のバージョンで利用可能なすべての ISO オプションを使用します。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーが[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに接続すると、サーバーはクライアントがネイティブ クライアント[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ODBC ドライバーを使用していることを検出し、いくつかのオプションをオンに設定します。  
  
 ステートメント自体はドライバーが実行します。ODBC アプリケーションはステートメントの実行に対して何の要求も行いません。 ISO オプションを設定することで、SQL Native Client ODBC ドライバーを使用する ODBC アプリケーションの移植性が高まります。これは、サーバーの動作が ISO 標準に準拠するためです。  
  
 DB-Library ベースのアプリケーションは、通常これらのオプションを有効にしません。 同じ SQL ステートメントを実行する場合、ODBC クライアントまたは DB-Library クライアント間で異なる動作を観察[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]するサイトでは、ネイティブ クライアント ODBC ドライバーの問題を指し示す必要はありません。 まず、ネイティブ クライアント ODBC ドライバで使用されるのと同じ SET オプションを使用して、DB-Library 環境でステートメントを再実行する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]必要があります。  
  
 SET オプションはユーザーやアプリケーションがいつでも有効または無効にできるので、ストアド プロシージャやトリガーの開発者は、上記の SET オプションを有効にした場合と無効にした場合の両方で、開発したプロシージャやトリガーをテストする必要があります。 これにより、プロシージャやトリガーの起動時に、接続に設定されているオプションに関係なく、プロシージャやトリガーが適切に動作することを確認できます。 これらのオプションのいずれかについて特定の設定が必要なトリガーやストアド プロシージャは、そのトリガーやストアド プロシージャの起動時に SET ステートメントを実行する必要があります。 この SET ステートメントは、トリガーやストアド プロシージャが実行されている間だけ有効になり、トリガーやストアド プロシージャが終了すると元の設定が復元されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続しているときは、4 番目の SET オプションの CONCAT_NULL_YIELDS_NULL も有効になります。 ネイティブ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは、データ ソースまたは[SQL ドライバ接続または SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)のいずれかで AnsiNPW=NO が指定されている場合に、これらのオプション[を](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)設定しません。  
  
 前述の ISO オプションと同様[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に、データ ソースまたは**SQLDriverConnect**または**SQLBrowseConnect**のいずれかで quotedID=NO が指定されている場合、ネイティブ クライアント ODBC ドライバはQUOTED_IDENTIFIER オプションをオンにしません。  
  
 ドライバーが SET オプションの現在の状態を確認できるようにするために、ODBC アプリケーションでは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] SET ステートメントを使用して SET オプションを設定しないようにします。 これらのオプションを設定する場合は、データ ソースまたは接続オプションのみを使用するようにします。 アプリケーションが SET ステートメントを実行した場合、ドライバーは不正な SQL ステートメントを生成する可能性があります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;ステートメントの実行](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [コネクト](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
