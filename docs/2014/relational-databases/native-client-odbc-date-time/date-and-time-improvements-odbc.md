---
title: 日付と時刻の強化 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207007"
---
# <a name="date-and-time-improvements-odbc"></a>日付と時刻の強化機能 (ODBC)
  
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、新しい日付と時刻のデータ型が導入されました。 このセクションでは、これらの新しい型がネイティブクライアント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で拡張として公開されるしくみについて説明します。 Native Client による[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しい日付と時刻のデータ型のサポートの概要については、「[日付と時刻の機能強化](../native-client/features/date-and-time-improvements.md)」を参照してください。 ODBC の日付と時刻のサポートを示すサンプルについては、「[日付と時刻の型の使用](../native-client-odbc-how-to/use-date-and-time-types.md)」を参照してください。  
  
 日付と時刻のデータ型に関する一般的な情報については、「 [datetime &#40;transact-sql&#41;](/sql/t-sql/data-types/datetime-transact-sql)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ODBC の日付/時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付と時刻のデータ型をサポートする ODBC 型について説明します。  
  
 [ODBC&#41;&#40;メタデータ](../../database-engine/dev-guide/metadata-odbc.md)  
 実装パラメーター記述子 (IPD) フィールドと実装行記述子 (IRD) フィールドに返される情報、および `SQLColumns` と `SQLProcedureColumns` によって返される列のメタデータについて説明します。 また、`SQLGetTypeInfo` によって返される、データ型のメタデータについても説明します。  
  
 [ODBC&#41;&#40;の datetime データ型の変換](datetime-data-type-conversions-odbc.md)  
 datetime 値と datetimeoffset 値の間で変換を行う方法について説明します。  
  
 [sql_variant による日付型と時刻型のサポート](sql-variant-support-for-date-and-time-types.md)  
 SQL_VARIANT 関数による機能強化された日付と時刻のサポートについて説明します。  
  
 [OLE DB および ODBC の &#40;、強化された日付/時刻型に対する一括コピーの変更&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 一括コピー操作をサポートする日付または時刻の機能強化について説明します。  
  
 [以前の SQL Server バージョン &#40;ODBC&#41;の日付と時刻の型の動作の強化](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 機能強化された日付と時刻を使用するクライアントアプリケーションが古いバージョンのと通信する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、および以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client でコンパイルされたクライアントが、機能強化された日付と時刻の機能をサポートするサーバーにコマンドを送信する場合に想定される動作について説明します。  
  
 [ODBC API による機能強化された日付と時刻のサポート](odbc-api-support-for-enhanced-date-and-time-features.md)  
 機能強化された日付と時刻をサポートする ODBC 関数の一覧を示します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
