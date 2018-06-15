---
title: SQLTransact (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d55151795d4f25edf08c5f1b3efa02499996c510
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903697"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 すべてのステートメント ハンドルのすべてのアクティブな操作をコミットまたはロールバック操作の要求 (*hstmt*s) 接続または、環境ハンドルに関連付けられているすべての接続に関連付けられた*henv*です。 **SQLTransact**にあるデータ ソースに対してのみ機能[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)です。  
  
 手動モードのときに、コミットが失敗した場合、トランザクションが消えないです。トランザクションをロールバックまたはコミット操作を再試行することができます。 コミット操作は、自動トランザクション モードのときに失敗すると、トランザクションは自動的にロールバックします。トランザクションは、非アクティブにすることはできません。  
  
 詳細については、次を参照してください。 [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)で、 *ODBC プログラマ リファレンス*です。
