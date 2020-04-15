---
title: コネクトオプション (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2af208663f1e91250faad0ca9538b76bcec43b06
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301503"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: 部分  
  
 ODBC API 準拠: レベル 1  
  
 接続の側面を制御するオプションを設定します。 この関数は部分的にサポートされています: ドライバーは*fOption*引数のすべての値をサポートしていますが *、fOption*引数SQL_TXN_ISOLATIONの一部の*vParam*値をサポートしていません。  
  
 次の表では **、SQLSetConnect オプション**のビジュアル フォックス プロ ODBC ドライバー実装に固有の動作を持つ引数のみを説明します。  
  
|*オプション*|解説|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|SQL_AUTOCOMMIT_OFFを選択した場合、アプリケーションは[SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)を使用してトランザクションを明示的にコミットまたはロールバックする必要があります。Visual FoxPro ODBC ドライバーは、完了時に、トランザクション可能なステートメントを自動的にコミットしません。 ステートメントがトランザクション可能な場合、ドライバーはトランザクションを開始します。|  
|SQL_CURRENT_QUALIFIER|完全に修飾された[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)名、または空[きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)が 0 個以上含まれているディレクトリへの完全修飾パスを指定できます。|  
|SQL_LOGINTIMEOUT|"ドライバに対応していません" というエラーを返します。|  
|SQL_CURSORS|"ドライバに対応していません" というエラーを返します。|  
|SQL_PACKET_SIZE|"ドライバに対応していません" というエラーを返します。|  
|SQL_TXN_ISOLATION|ドライバはSQL_TXN_READ_COMMITTEDのみを許可します。<br /><br /> 次の*vParam*はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 詳細については *、ODBC プログラマ リファレンス*の[「SQLSetConnect オプション](../../odbc/reference/syntax/sqlsetconnectoption-function.md)」を参照してください。
