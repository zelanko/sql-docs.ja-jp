---
title: SQLGetStmtOption (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cb9e9178d7b90afaaa5cd324f79459a14a2dcc6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 ステートメント オプションの現在の設定を返します。  
  
|*fOption*|返します。|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|現在のレコード数のブックマークは、32 ビット整数値|  
|SQL_ROW_NUMBER|結果内の現在の行の位置を示す 32 ビット整数の設定|  
|SQL_TRANSLATE_DLL|エラー:「ドライバー対応していない」|  
  
 Visual FoxPro ODBC ドライバーには、Dll の変換がありません。  
  
 詳細については、次を参照してください。 [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)で、 *ODBC プログラマ リファレンス*です。
