---
title: 行動の変化 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e4a433531d90eb0f89d9a5e446464b13fd02526
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283442"
---
# <a name="behavioral-changes"></a>動作の変更
動作の変更とは、インターフェイスの*構文*は同じままですが、*セマンティクス*が変更された変更です。 これらの変更については、ODBC 2 で使用される機能。*x*は ODBC 3 の同じ機能とは動作が異なります。*x .*  
  
 アプリケーションが ODBC 2 を示すかどうか。*x*動作または ODBC 3。*x*の動作は、SQL_ATTR_ODBC_VERSION環境属性によって決定されます。 この 32 ビット値は、ODBC 2 を表示するSQL_OV_ODBC2に設定されています。*x*の動作を行い、odbc 3 を表示SQL_OV_ODBC3。*x*の動作。  
  
 SQL_ATTR_ODBC_VERSION環境属性は、 **SQLSetEnvAttr**の呼び出しによって設定されます。 アプリケーションが**SQLAllocHandle**を呼び出して環境ハンドルを割り当てた後、アプリケーションは直ちに**SQLSetEnvAttr**を呼び出して、動作を設定する必要があります。 (結果として、割り当てられたバージョンなしの状態で環境ハンドルを記述する新しい環境状態が存在します)。詳細については、「[付録 B : ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。  
  
 アプリケーションは、SQL_ATTR_ODBC_VERSION環境属性でどのような動作を示すのかを示しますが、この属性は、ODBC 2 とのアプリケーションの接続には影響しません。*x*または ODBC 3。*x*ドライバ。 ODBC 3。*x*アプリケーションは、ODBC 2 のいずれかに接続できます。*x*または 3.*x*ドライバ、環境属性の設定に関係なく。  
  
 ODBC 3.*x*アプリケーションは **、SQLAllocEnv**を呼び出してはいけません。 その結果、ドライバー マネージャーは **、SQLAllocEnv**への呼び出しを受信した場合、ODBC 2 としてアプリケーションを認識します。*x*アプリケーション。  
  
 SQL_ATTR_ODBC_VERSION属性は、ODBC 3 の 3 つの異なる側面に影響します。*x*ドライバの動作:  
  
-   SQLSTATE  
  
-   日付、時刻、およびタイム・スタンプのデータ・タイプ  
  
-   **SQLTables**の*引数のカタログ名*は、ODBC 3 で検索パターンを受け入れます。*x*は、ODBC 2 では使用できません。*x*  
  
 SQL_ATTR_ODBC_VERSION環境属性の設定は **、SQLSetParam**または**SQLBindParam**には影響しません。 **また**、このビットの影響を受けません。 **SQLColAttribute**は、ODBC のバージョン (日付の種類、精度、スケール、および長さ) の影響を受ける属性を返しますが、意図された動作は*FieldIdentifier*引数の値によって決定されます。 *フィールド識別子*がSQL_DESC_TYPEに等しい場合 **、ODBC** 3 が返されます。日付、時刻、タイムスタンプの*x*コード。*フィールド識別子*がSQL_COLUMN_TYPEに等しい場合**は**、ODBC 2 を返します。*日付*、時刻、タイムスタンプの x コード。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLSTATE マッピング](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [datetime データ型の変更](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
