---
title: デスクトップデータベースドライバーの診断 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99603c047e77d3cd3e077c1b07c2192eeb65f93c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303483"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>デスクトップ データベース ドライバーの診断
ドライバーマネージャーによって確認または部分的にチェックされていないすべてのエラーと警告は、ドライバーによって処理されます。 また、このドライバーは、ネイティブエラー、またはデータソースから返されたエラーを SQLSTATEs にマップします。 *ODBC プログラマーズリファレンス*に記載されている各関数には、条件とメッセージを指定する "診断" セクションが含まれています。  
  
 アプリケーションは、SQLSTATE、ネイティブエラーコード、および診断メッセージを取得するために**SQLGetDiagRec**を呼び出します。 **SQLGetDiagField**を呼び出し、フィールドを指定すると、個々の診断フィールドが取得されます。 次の表に、診断識別子のサポートレベルを示します。  
  
|DiagIdentifiers|サポート レベル|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|サポートされていません|  
|SQL_DIAG_CLASS_ORIGIN|サポートされています。 このドライバーのバージョン3.0 以降では、常に "ODBC 3.0" を使用します。|  
|SQL_DIAG_COLUMN_NUMBER|サポートされています|  
|SQL_DIAG_CURSOR_ROW_COUNT|サポートされていません|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|サポートされていません|  
|SQL_DIAG_MESSAGE_TEXT|サポートされています|  
|SQL_DIAG_NATIVE|サポートされています|  
|SQL_DIAG_NUMBER|サポートされています|  
|SQL_DIAG_RETURNCODE|サポートされますが、ドライバーマネージャーによって実装されます。|  
|SQL_DIAG_ROW_COUNT|サポートされています|  
|SQL_DIAG_ROW_NUMBER|サポートされています|  
|SQL_DIAG_SERVER_NAME|サポートされていません|  
|SQL_DIAG_SQLSTATE|サポートされています|  
|SQL_DIAG_SUBCLASS_ORIGIN|サポートされています|
