---
title: SQLSetConnectOption (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301503"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 部分的  
  
 ODBC API の準拠: レベル1  
  
 接続の側面を制御するオプションを設定します。 この関数は部分的にサポートされています。ドライバーは*foption*引数のすべての値をサポートしていますが、 *foption*引数 SQL_TXN_ISOLATION の*vparam*値の一部をサポートしていません。  
  
 次の表では、 **SQLSetConnectOption**の VISUAL FoxPro ODBC ドライバーの実装に固有の動作を持つ引数のみについて説明します。  
  
|*fOption*|Remarks|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|SQL_AUTOCOMMIT_OFF を選択した場合、アプリケーションは[Sqltransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)を使用してトランザクションを明示的にコミットまたはロールバックする必要があります。Visual FoxPro ODBC ドライバーは、完了時に不可能ステートメントを自動的にコミットしません。 ステートメントが不可能の場合、ドライバーはトランザクションを開始します。|  
|SQL_CURRENT_QUALIFIER|には、完全修飾[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)名または0個以上の[フリーテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)を含むディレクトリへの完全修飾パスを指定できます。|  
|SQL_LOGINTIMEOUT|"ドライバーがサポートされていません" エラーを返します。|  
|SQL_CURSORS|"ドライバーがサポートされていません" エラーを返します。|  
|SQL_PACKET_SIZE|"ドライバーがサポートされていません" エラーを返します。|  
|SQL_TXN_ISOLATION|ドライバーは SQL_TXN_READ_COMMITTED のみを許可します。<br /><br /> 次の*Vparam*はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) 」を参照してください。
