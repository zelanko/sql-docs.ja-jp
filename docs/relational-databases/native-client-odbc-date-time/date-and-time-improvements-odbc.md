---
title: "日付と時刻の強化 (ODBC) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aeb11ff29e82ff48147ee5346f7b1f864cdee32
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="date-and-time-improvements-odbc"></a>日付と時刻の強化 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、新しい日付と時刻のデータ型が導入されました。 このセクションでは、拡張機能としてこれらの新しい型を公開する方法について説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client です。 概要については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client、新しい日付と時刻のデータ型のサポートを参照してください[日付と時刻の強化](../../relational-databases/native-client/features/date-and-time-improvements.md)です。 ODBC 日付/時刻のサポートを示すサンプルについては、次を参照してください。[を使用して日付と時刻型](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md)です。  
  
 一般的な日付と時刻データ型については、次を参照してください。 [datetime &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ODBC の日付/時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付と時刻のデータ型をサポートする ODBC 型について説明します。  
  
 [メタデータ &#40;ODBC&#41;](http://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 実装パラメーター記述子 (IPD) と実装行記述子 (IRD) フィールドに加え、によって返される列のメタデータに返される情報について説明します**SQLColumns**と**SQLProcedureColumns**. によって返されるデータ型のメタデータについても説明します。 **SQLGetTypeInfo**です。  
  
 [datetime データ型変換 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 datetime 値と datetimeoffset 値の間で変換を行う方法について説明します。  
  
 [sql_variant による日付型と時刻型のサポート](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 SQL_VARIANT 関数による機能強化された日付と時刻のサポートについて説明します。  
  
 [強化された日付と時刻型 &#40; OLE DB と ODBC &#41; の一括コピーの変更](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 一括コピー操作をサポートする日付または時刻の機能強化について説明します。  
  
 [強化された日付と時刻型の動作で以前バージョンの SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 以前のバージョンの機能強化された日付と時刻を使用してクライアント アプリケーションと通信するときに想定される動作について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、クライアントが、古いバージョンのでコンパイルされたときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーにネイティブ クライアントはコマンドを送信強化された日付と時刻の機能をサポートします。  
  
 [ODBC API による機能強化された日付と時刻のサポート](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 機能強化された日付と時刻をサポートする ODBC 関数の一覧を示します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
