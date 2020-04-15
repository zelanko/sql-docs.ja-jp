---
title: ODBC カーソル ライブラリ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 93c85bc943d1a6a081cbea6bbeae40ba85aeffc5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305403"
---
# <a name="odbc-cursor-library"></a>ODBC カーソル ライブラリ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC ドライバの中には、デフォルトのカーソル設定しかサポートしなかないものもあります。これらのドライバーは、位置指定カーソル操作をサポートしていません( **SQLSetPos**など )。 ODBC カーソル ライブラリは、通常はブロック カーソルや静的カーソルがサポートされないドライバーに対して、これらのカーソルを実装するときに使用される MDAC (Microsoft Data Access Components) のコンポーネントです。 カーソル ライブラリは、作成するカーソルに対して、位置指定された UPDATE ステートメントと DELETE ステートメントと**SQLSetPos**も実装します。  
  
 ODBC カーソル ライブラリは、ODBC ドライバー マネージャーと ODBC ドライバーの中間層として実装されます。 ODBC ドライバー マネージャーは、ODBC カーソル ライブラリが読み込まれると、すべてのカーソル関連コマンドをドライバーではなく、読み込んだカーソル ライブラリにルーティングします。 カーソル ライブラリでは、基になるドライバーから結果セット全体をフェッチし、その結果セットをクライアントにキャッシュすることにより、カーソルを実装します。 ODBC カーソル ライブラリを使用しているときは、アプリケーションではカーソル ライブラリのカーソル機能だけをサポートし、基になるドライバーの追加のカーソル機能はサポートしません。  
  
 ドライバー自体は ODBC カーソル ライブラリよりも多くの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソル機能をサポートするため、ネイティブ クライアント ODBC ドライバーで ODBC カーソル ライブラリを使用する必要はほとんどありません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーで ODBC カーソル ライブラリを使用する唯一の理由は、ドライバーがサーバー カーソルを介してカーソルサポートを実装し、サーバー カーソルがすべての SQL ステートメントをサポートしていないためです。 ストアド プロシージャ、バッチ、または COMPUTE、COMPUTE BY、FOR BROWSE、INTO などを含む SQL ステートメントで静的カーソルを使用する必要がある場合は、ODBC カーソル ライブラリの使用を検討してください。 ただし、カーソル ライブラリを使用する場合、結果セット全体がクライアントにキャッシュされるので、大量のメモリが使用され、パフォーマンスが低下することがあるので注意が必要です。  
  
 アプリケーションは[、SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を使用して、データ ソースに接続する前にSQL_ATTR_ODBC_CURSORS接続属性を設定することで、接続ごとにカーソル ライブラリを呼び出します。 SQL_ATTR_ODBC_CURSORS には、次の 3 つの値のいずれかを設定します。  
  
 SQL_CUR_USE_ODBC  
 ネイティブ クライアント ODBC ドライバー[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]でこのオプションを設定すると、ODBC カーソル ライブラリは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーのネイティブ カーソル サポートをオーバーライドします。 接続で使用できるのは、カーソル ライブラリでサポートされているカーソルのみで、サーバー カーソルは使用できません。  
  
 SQL_CUR_USE_DRIVER   
 このオプションを設定すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ・クライアントの ODBC ドライバーにネイティブのすべてのカーソル・サポートを接続に使用できます。 この場合、ODBC カーソル ライブラリは使用できません。 すべてのカーソルはサーバー カーソルとして実装されます。  
  
 SQL_CUR_USE_IF_NEEDED   
 このオプションを設定すると、ネイティブ クライアント ODBC ドライバで使用した場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のSQL_CUR_USE_DRIVERと同じ効果が得られます。 接続時に、ODBC ドライバ マネージャは、接続先の ODBC ドライバが[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)のSQL_FETCH_PRIOR オプションをサポートしているかどうかをテストします。 ドライバーでこのオプションがサポートされていない場合、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込みます。 サポートされている場合、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込みません。この場合、アプリケーションではドライバーのネイティブ サポートが使用されます。 ネイティブ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーはSQL_FETCH_PRIORサポートするため、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込みません。  
  
 カーソル ライブラリにより、アプリケーションはスクロール可能なカーソルや更新可能なカーソルを使用できるだけでなく、1 つの接続に対して複数のアクティブ ステートメントを使用できます。 この機能をサポートする場合は、カーソル ライブラリを読み込む必要があります。 カーソル ライブラリの使用方法を指定するには[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を使用し、カーソルの種類、同時実行性、および行セットのサイズを指定する[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を使用します。  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
