---
title: dBASE データ タイプ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60240eb9763d2d0b581765bde3a6d0958567f08e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dbase-data-types"></a>dBASE データ型
次の表では、dBASE データ型を ODBC SQL データ型にマップする方法を示します。 すべての ODBC SQL データ型がサポートされていることに注意してください。  
  
|dBASE データ型|ODBC データ型|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|[DATE]|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|論理|SQL_BIT|  
|メモ|SQL_LONGVARCHAR|  
|数値 (BCD)|SQL_DOUBLE|  
|OLEOBJECT [1]|SQL_LONGBINARY|  
  
 DBASE バージョン 5 にのみ有効期間を [1] です。*x*  
  
 DBASE の有効桁数 III により、数値を 2 桁の指数部を有する dBASE IV 数の最大 3 桁の指数部です。 数値がテキストとして格納される、ためを数値に変換されます。 変換する数値が収まらない場合、フィールドに予期しない結果が発生する可能性があります。  
  
 DBASE は、有効桁数で数値データ型を指定する、小数点以下を許可しているときに、dBASE の ODBC ドライバーではサポートされません。 常に、dBASE の ODBC ドライバーは、15 文字の有効桁数と小数点以下桁数は、数値データ型の場合は 0 を返します。  
  
 ODBC の SQL_DOUBLE データ型には、ODBC dBASE ドライバー マップを使用して、数値データ型で作成された列です。 したがってこの列のデータは、丸め処理の対象です。 この動作は同じ数値データの型として dBASE (型 N) は Binary Coded Decimal (BCD)。  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC SQL データ型を返します。 付録 d のすべての変換、 *ODBC プログラマ リファレンス*このトピックの前半に示した ODBC SQL データ型はサポートされます。  
  
 次の表は、データ型、dBASE の制限事項を示します。  
  
|データ型|Description|  
|---------------|-----------------|  
|CHAR|ゼロの char 型の列を作成するか、未指定の長さが実際に 254 バイトの列を返します。|  
|暗号化データ|DBASE ドライバーでは、dBASE テーブルはサポートされません。|  
|論理|DBASE ドライバーは、論理列にインデックスを作成することはできません。|  
|メモ|メモ列の最大長は 65,500 バイトです。|  
  
 データ型に複数の制限事項は含まれて[データ型の制限事項](../../odbc/microsoft/data-type-limitations.md)です。
