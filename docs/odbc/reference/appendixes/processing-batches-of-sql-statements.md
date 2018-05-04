---
title: SQL ステートメントのバッチの処理 |Microsoft ドキュメント
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
- ODBC cursor library [ODBC], batches
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], batches
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- SQL statements [ODBC], batches
- batches [ODBC], processing batches of SQL statements
ms.assetid: 04b93ef9-11de-47a3-8bd8-ba963c42f182
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5815942713383251a5eeff0df7857809e18f7f38
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="processing-batches-of-sql-statements"></a>SQL ステートメントのバッチの処理
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは、SQL_ATTR_PARAMSET_SIZE ステートメント属性が 1 より大きい SQL ステートメントなど、SQL ステートメントのバッチをサポートしていません。 アプリケーションでは、カーソル ライブラリへの SQL ステートメントのバッチを送信する場合、結果は未定義です。
