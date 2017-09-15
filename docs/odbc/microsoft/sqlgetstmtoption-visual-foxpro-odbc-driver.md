---
title: "SQLGetStmtOption (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 601dd559d7bf13d1a12d032d8431a8c3fe0287d4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 ステートメント オプションの現在の設定を返します。  
  
|*FOption*|返します。|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|現在のレコード数のブックマークは、32 ビット整数値|  
|SQL_ROW_NUMBER|結果内の現在の行の位置を示す 32 ビット整数の設定|  
|SQL_TRANSLATE_DLL|エラー:「ドライバー対応していない」|  
  
 Visual FoxPro ODBC ドライバーには、Dll の変換がありません。  
  
 詳細については、次を参照してください。 [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)で、 *ODBC プログラマ リファレンス*です。
