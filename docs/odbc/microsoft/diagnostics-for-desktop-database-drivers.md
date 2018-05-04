---
title: デスクトップの診断データベース ドライバー |Microsoft ドキュメント
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
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23e5933bb5a17d4e870e6d50b8821b6407ccd277
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics-for-desktop-database-drivers"></a>デスクトップ データベース ドライバーの診断
すべてのエラーと警告いないチェックインまたはドライバー マネージャーによってを部分的にチェックは、ドライバーによって処理されます。 ドライバーもマップ ネイティブ エラー、またはデータ ソースによって SQLSTATEs に返されたエラー。 各関数に一覧表示、 *ODBC プログラマ リファレンス*条件とメッセージを指定する「診断」セクションが含まれています。  
  
 アプリケーションのコール**SQLGetDiagRec** SQLSTATE、ネイティブ エラー コード、および診断メッセージを取得します。 呼び出す**SQLGetDiagField**し、フィールドを指定するには、個々 の診断フィールドを取得します。 診断の識別子のサポートのレベルは、次の表に表示されます。  
  
|DiagIdentifiers|サポート レベル|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|サポートされていません|  
|SQL_DIAG_CLASS_ORIGIN|サポートされています。 常に"ODBC 3.0"のバージョン 3.0 と以降のこのドライバー。|  
|SQL_DIAG_COLUMN_NUMBER|Supported|  
|SQL_DIAG_CURSOR_ROW_COUNT|サポートされていません|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|サポートされていません|  
|SQL_DIAG_MESSAGE_TEXT|Supported|  
|SQL_DIAG_NATIVE|Supported|  
|SQL_DIAG_NUMBER|Supported|  
|SQL_DIAG_RETURNCODE|サポートされていますが、ドライバー マネージャーによって実装されています。|  
|SQL_DIAG_ROW_COUNT|Supported|  
|SQL_DIAG_ROW_NUMBER|Supported|  
|SQL_DIAG_SERVER_NAME|サポートされていません|  
|SQL_DIAG_SQLSTATE|Supported|  
|SQL_DIAG_SUBCLASS_ORIGIN|Supported|
