---
title: 日付と時刻の強化 (ODBC) |Microsoft ドキュメント
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
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19c4e63fc9e101379af2ac7b6bc859daa783ae6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178421"
---
# <a name="date-and-time-improvements-odbc"></a>日付と時刻の強化 (ODBC)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、新しい日付と時刻のデータ型が導入されました。 このセクションでは、拡張機能としてこれらの新しい型を公開する方法について説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client です。 概要については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client、新しい日付と時刻のデータ型のサポートを参照してください[日付と時刻の強化](../native-client/features/date-and-time-improvements.md)です。 ODBC 日付/時刻のサポートを示すサンプルについては、次を参照してください。[を使用して日付と時刻型](../native-client-odbc-how-to/use-date-and-time-types.md)です。  
  
 一般的な日付と時刻データ型については、次を参照してください。 [datetime &#40;TRANSACT-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ODBC の日付/時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付と時刻のデータ型をサポートする ODBC 型について説明します。  
  
 [メタデータ&#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 実装パラメーター記述子 (IPD) フィールドと実装行記述子 (IRD) フィールドに返される情報、および `SQLColumns` と `SQLProcedureColumns` によって返される列のメタデータについて説明します。 また、`SQLGetTypeInfo` によって返される、データ型のメタデータについても説明します。  
  
 [datetime データ型変換&#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 datetime 値と datetimeoffset 値の間で変換を行う方法について説明します。  
  
 [sql_variant による日付型と時刻型のサポート](sql-variant-support-for-date-and-time-types.md)  
 SQL_VARIANT 関数による機能強化された日付と時刻のサポートについて説明します。  
  
 [強化された日付と時刻型に対して変更のコピーを一括&#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 一括コピー操作をサポートする日付または時刻の機能強化について説明します。  
  
 [強化された日付と時刻は、以前のバージョンの SQL Server での動作を入力&#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 以前のバージョンの機能強化された日付と時刻を使用してクライアント アプリケーションと通信するときに想定される動作について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、クライアントが、古いバージョンのでコンパイルされたときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーにネイティブ クライアントはコマンドを送信強化された日付と時刻の機能をサポートします。  
  
 [ODBC API による機能強化された日付と時刻のサポート](odbc-api-support-for-enhanced-date-and-time-features.md)  
 機能強化された日付と時刻をサポートする ODBC 関数の一覧を示します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
