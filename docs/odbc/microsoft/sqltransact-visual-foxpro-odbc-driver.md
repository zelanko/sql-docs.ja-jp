---
title: SQLTransact (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f787e04610187011b12c25ce738432066120365
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 すべてのステートメント ハンドルのすべてのアクティブな操作をコミットまたはロールバック操作の要求 (*hstmt*s) 接続または、環境ハンドルに関連付けられているすべての接続に関連付けられた*henv*です。 **SQLTransact**にあるデータ ソースに対してのみ機能[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)です。  
  
 手動モードのときに、コミットが失敗した場合、トランザクションが消えないです。トランザクションをロールバックまたはコミット操作を再試行することができます。 コミット操作は、自動トランザクション モードのときに失敗すると、トランザクションは自動的にロールバックします。トランザクションは、非アクティブにすることはできません。  
  
 詳細については、次を参照してください。 [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)で、 *ODBC プログラマ リファレンス*です。
