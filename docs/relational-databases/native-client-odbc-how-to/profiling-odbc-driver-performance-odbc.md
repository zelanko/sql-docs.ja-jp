---
title: ODBC ドライバー パフォーマンスに関するトピック (ODBC) をプロファイリング |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f06a703058b1caf05e2df81338d2d26e24082d3e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074935"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>ODBC ドライバーのパフォーマンスのプロファイル (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーには、ドライバーのパフォーマンスをプロファイルするための、ドライバー固有の 2 つのオプションが用意されています。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーはファイルにパフォーマンスの統計情報を記録することができます。 ログ ファイルはタブで区切られており、Microsoft Excel など、タブ区切りのファイルをサポートする任意のスプレッドシートで分析できます。  
  
 ドライバーは、実行時間の長いクエリ (指定した時間内にサーバーから応答が得られないクエリ) もログに記録できます。 プログラマとデータベース管理者は、これらのクエリを後で分析できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ドライバーのパフォーマンス データをプロファイル&#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [ログ クエリの実行時間の長い&#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>参照  
 [ODBC の使用法に関するトピック](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
