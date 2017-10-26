---
title: "SQLExtendedFetch (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
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
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25a9e0b16551ca27a6818fcfd890e56aeabfb44b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API への準拠: レベル 2  
  
 ような[SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md)列ごとに配列を使用して複数の行が返されます。 結果セットは前方スクロールし、旧バージョンとスクロールが静的、順方向専用カーソルが定義されている場合に行んだことができます。  
  
 既定では、Visual FoxPro ODBC ドライバーは FoxPro テーブルの削除済みとしてマークされている行を返しません。 結果セットのカーソルでは、削除対象としてマークが、テーブルから削除されていない行は含まれません。 使用してこの動作を変更することができます、[削除設定](../../odbc/microsoft/set-deleted-command.md)コマンド。  
  
 詳細については、次を参照してください。 [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md)で、 *ODBC プログラマ リファレンス*です。

