---
title: "接続ハンドルの割り当て |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a030fc1cf17afcac67ba8cc3bf1d0004fedc1d45
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="allocating-a-connection-handle"></a>接続ハンドルの割り当て
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションからデータ ソースまたはドライバーに接続する前に、接続ハンドルを割り当てる必要があります。 呼び出すことによってこれは、 **SQLAllocHandle**で、 *HandleType*パラメーターを sql_handle_dbc として設定し、 *InputHandle*初期化環境ハンドルを指すです。  
  
 接続の特性は、接続属性の設定により制御されます。 たとえば、トランザクションは接続レベルで行われるので、トランザクション分離レベルは 1 つの接続属性になります。 同様に、ログイン タイムアウト、つまり接続試行がタイムアウトするまで待機する秒数も接続属性です。  
  
 接続属性が設定されて[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)でその現在の設定が取得および[SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)です。 場合**SQLSetConnectAttr**は接続を試行する前に呼び出されると、ODBC ドライバー マネージャーは接続構造に属性を格納し、接続処理の一部としてドライバーに設定します。 接続属性の中には、アプリケーションが接続を試行する前に設定しなければならないものも、接続の確立後に設定できるものもあります。 たとえば、SQL_ATTR_ODBC_CURSORS は接続前に設定する必要がありますが、SQL_ATTR_AUTOCOMMIT は接続後に設定できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降に対してアプリケーションを実行している場合、表形式のデータ ストリーム (TDS) のネットワーク パケット サイズを再設定すると、パフォーマンスが向上することがあります。 サーバーに設定されている既定のパケット サイズは 4 KB です。 パフォーマンスが最も高くなるのは、通常、パケット サイズが 4 ～ 8 KB のときです。 テストにより、他のパケット サイズの方がパフォーマンスが高くなることがわかった場合、アプリケーションではパケット サイズを再設定できます。 ODBC アプリケーションがこれを呼び出すことによって接続する前に行う**SQLSetConnectAttr** SQL_ATTR_PACKET_SIZE オプションを使用します。 パケット サイズを大きくすることでパフォーマンスが向上するアプリケーションもありますが、通常、8 KB を超えるパケット サイズを指定して向上するパフォーマンスはごくわずかです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーには、アプリケーションが機能強化のために使用できる拡張接続属性の数が含まれています。 拡張属性の一部にはデータ ソースで指定されるオプションと同じものを制御するものがあります。このような属性を使用すると、常に、データ ソースで設定されたオプションよりも、拡張属性のオプションが優先されます。 たとえば、アプリケーションで引用符で囲まれた識別子を使用する場合は、ドライバー固有の属性である SQL_COPT_SS_QUOTED_IDENT を SQL_QI_ON に設定すると、データ ソースの設定とは関係なく、識別子を引用符で囲むというオプションが常に有効になります。  
  
## <a name="see-also"></a>参照  
 [SQL Server &#40;ODBC&#41; と通信します。](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
