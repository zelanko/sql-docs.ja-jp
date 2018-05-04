---
title: 動作の変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51737ccc21f8ee4d3d1943433f88393d4847ea8a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="behavioral-changes"></a>動作の変更
動作の変更は、これらの変更を*構文*インターフェイスは同じですが、*セマンティクス*が変更されました。 これらの変更、ODBC 2 で使用されている機能です。*x* ODBC 3 で同じ機能の動作は異なります*。x*です。  
  
 かどうか、アプリケーションでは、ODBC 2 が発生します。*x*動作または ODBC 3 *。x*動作また環境属性によって決定されます。 この 32 ビット値は、ODBC 2 が発生すること SQL_OV_ODBC2 に設定されます。*x*動作、および ODBC 3 が発生する SQL_OV_ODBC3 *。x*動作します。  
  
 呼び出しによって、また環境属性が設定されて**SQLSetEnvAttr**です。 アプリケーションが呼び出す後**SQLAllocHandle**環境ハンドルを割り当てるに呼び出す必要があります**SQLSetEnvAttr**すぐに動作を設定することが発生します。 (その結果は、新しい環境の状態を割り当て済みでは、versionless 環境ハンドルを記述する状態。)詳細については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
 アプリケーションでは、また環境属性が属性は、どのような動作は、ODBC 2 とアプリケーションの接続に影響を与えませんを示しています。*x*または ODBC 3 *。x*ドライバー。 ODBC 3 です。*x*アプリケーションを ODBC 2 との接続のことができます*。x*または 3 つです*。x*環境属性の設定内容に関係なく、ドライバーです。  
  
 ODBC 3 です。*x*アプリケーションは呼び出さないで**SQLAllocEnv**です。 ドライバー マネージャーへの呼び出しを受信した場合、結果として**SQLAllocEnv**、ODBC 2 としてアプリケーションを認識します*。x*アプリケーションです。  
  
 また属性では、ODBC 3 の 3 つのさまざまな側面に影響します。*x*ドライバーの動作。  
  
-   SQLSTATEs  
  
-   日付、時刻、およびタイムスタンプのデータ型  
  
-   *CatalogName*引数**SQLTables** ODBC 3 内の検索パターンを受け入れます*。x*、ODBC 2 ではなく*。x*  
  
 また環境属性の設定には影響しません**SQLSetParam**または**SQLBindParam**です。 **SQLColAttribute**も受けませんこのビットです。 **SQLColAttribute**の影響を受ける属性を返します、ODBC (date 型、有効桁数、小数点以下桁数、および長さ) のバージョンで目的の動作の値によって決まります、 *FieldIdentifier*引数。 ときに*FieldIdentifier* SQL_DESC_TYPE、等しく**SQLColAttribute** ODBC 3 が返されます*。x*日付、時刻、およびタイムスタンプのコードと*FieldIdentifier* SQL_COLUMN_TYPE、等しく**SQLColAttribute** ODBC 2 を返します*。x*日付、時刻、およびタイムスタンプのコード。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLSTATE マッピング](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [datetime データ型の変更](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
