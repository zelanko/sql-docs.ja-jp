---
title: "datetime データ型変換 (ODBC) |Microsoft ドキュメント"
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
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 065c030e38e588dbc1068ead291f0ac4f5a6a179
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="datetime-data-type-conversions-odbc"></a>datetime データ型変換 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  次の変換は、ODBC によって既に定義されているか、ODBC の一貫性がある拡張機能です。 各プロバイダーによって提供される変換は、プロバイダーが管理するコミュニティによって決まるので、プロバイダー間で一貫性がないことがよくあります。 角かっこで囲まれている値は省略可能です。  
  
-   datetime 型の文字列の形式は 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]' です。  
  
-   time 型の文字列の形式は 'hh:mm:ss[.9999999]' です。  
  
-   date 型の文字列の形式は 'yyyy-mm-dd' です。  
  
 文字列からの変換では、空白文字やフィールドの幅を柔軟に処理できます。 詳細についてを参照してください「データ形式: 文字列とリテラルをデータする」の[ODBC の日付と時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)です。  
  
 一般的な変換規則を次に示します。  
  
-   時刻が存在しなくても受信側が時刻を格納できる場合、時刻は 0 に設定されます。  
  
-   日付が存在しなくても受信側が日付を格納できる場合、現在の日付が使用されます。  
  
-   クライアントが使用しているデータ型にタイム ゾーンが存在しなくても、サーバーがタイム ゾーンを格納できる場合、日付はクライアントのタイム ゾーンで格納されます。 これはサーバーの動作とは異なることに注意してください。  
  
-   サーバーの型にタイム ゾーンが存在しなくても、クライアントの型にタイム ゾーンがある場合、時刻は UTC に変換されてからサーバーに格納されます。  
  
-   時刻はあるが、受信側が時刻を格納できない場合、時刻部分は無視されます。  
  
-   日付はあるが、受信側が日付を格納できない場合、日付部分は無視されます。  
  
-   C データ型から SQL データ型に変換する際に秒または秒の小数部の切り捨てが発生すると、"Datetime フィールド オーバーフロー" というメッセージで SQLSTATE 22008 の診断レコードが生成されます。  
  
-   SQL データ型から C データ型に変換する際に秒または秒の小数部の切り捨てが発生すると、"分数が切り捨てられました" というメッセージで SQLSTATE 01S07 の診断レコードが生成されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [C から SQL への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 C 型から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付型または時刻型に変換する際に考慮する問題を示します。  
  
 [SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付型または時刻型から C 型に変換する際に考慮する問題を示します。  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
