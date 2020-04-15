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
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2dd801988343ded46305665ab2a99aa4e7d76cba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298632"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: 部分  
  
 ODBC API 準拠: レベル 1  
  
 接続オプションの現在の設定を返します。 この関数は部分的にサポートされています: ドライバーは*fOption*引数のすべての値をサポートしていますが *、fOption*引数SQL_TXN_ISOLATIONの一部の*vParam*値をサポートしていません。  
  
 次の表では **、SQLGetConnectOption**の Visual FoxPro ODBC ドライバー実装に固有の動作を持つ引数のみを説明します。  
  
|*オプション*|解説|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|SQL_AUTOCOMMIT_OFFを選択した場合、アプリケーションは[SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)を使用してトランザクションを明示的にコミットまたはロールバックする必要があります。Visual FoxPro ODBC ドライバーは、完了時に、トランザクション可能なステートメントを自動的にコミットしません。 ステートメントがトランザクション可能な場合、ドライバーはトランザクションを開始します。|  
|SQL_CURRENT_QUALIFIER|完全に修飾されたデータベース (.dbc ファイル) 名、またはゼロ個以上のテーブル (.dbf ファイル) を含むディレクトリへの完全修飾パスを指定できます。|  
|SQL_LOGINTIMEOUT|"ドライバが対応していません" というエラーを返します。|  
|SQL_CURSORS|"ドライバが対応していません" というエラーを返します。|  
|SQL_PACKET_SIZE|"ドライバが対応していません" というエラーを返します。|  
|SQL_TXN_ISOLATION|ドライバはSQL_TXN_READ_COMMITTEDのみを許可します。<br /><br /> 次の*vParam*はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 詳細については *、ODBC プログラマ リファレンス*の「 [SQLGetConnect オプション](../../odbc/reference/syntax/sqlgetconnectoption-function.md)」を参照してください。
