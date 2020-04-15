---
title: 日付と時刻の改善 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94a9b8517ebd2539250995fea896c53a376fc65d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301763"
---
# <a name="date-and-time-improvements-odbc"></a>日付と時刻の強化機能 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、新しい日付と時刻のデータ型が導入されました。 このセクションでは、これらの新しい型がネイティブ クライアントで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張機能として公開される方法について説明します。 新しい日付と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時刻のデータ型のネイティブ クライアント サポートの概要については、「[日付と時刻の向上](../../relational-databases/native-client/features/date-and-time-improvements.md)」を参照してください。 ODBC 日付/時刻サポートの例については、「[日付と時刻の種類を使用](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md)する」を参照してください。  
  
 日付と時刻のデータ型に関する一般的な情報については、「[datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ODBC の日付/時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付と時刻のデータ型をサポートする ODBC 型について説明します。  
  
 [ODBC&#41;&#40;メタデータ](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 実装パラメーター記述子 (IPD) フィールドおよび実装行記述子 (IRD) フィールドに返される情報、および SQLColumns および**SQLProcedureColumns**によって返される列メタデータについて説明**します**。 また **、SQLGetTypeInfo**によって返されるデータ型メタデータについても説明します。  
  
 [ODBC&#41;&#40;日付時刻データ型変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 datetime 値と datetimeoffset 値の間で変換を行う方法について説明します。  
  
 [sql_variant による日付型と時刻型のサポート](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 SQL_VARIANT 関数による機能強化された日付と時刻のサポートについて説明します。  
  
 [OLE DB および ODBC&#41;&#40;拡張された日付と時刻の種類に対する一括コピーの変更](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 一括コピー操作をサポートする日付または時刻の機能強化について説明します。  
  
 [ODBC&#41;の以前のバージョン&#40;の日付と時刻の種類の動作が強化されました。](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 拡張された日付と時刻の機能を使用するクライアント アプリケーションが古いバージョンの と通信するとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および古いバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client でコンパイルされたクライアントが、拡張された日時機能をサポートするサーバーにコマンドを送信する場合の予期される動作について説明します。  
  
 [ODBC API による機能強化された日付と時刻のサポート](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 機能強化された日付と時刻をサポートする ODBC 関数の一覧を示します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
