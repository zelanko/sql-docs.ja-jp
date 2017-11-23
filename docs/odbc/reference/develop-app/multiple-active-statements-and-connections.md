---
title: "複数のアクティブなステートメントとの接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bff1b38ffb11cfd92b158e985dc6eaa45af9958c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="multiple-active-statements-and-connections"></a>複数のアクティブなステートメントとの接続
一部のドライバーと Dbms ステートメントと同時にアクティブにできる接続の数を制限します。 これらの数値はいずれかのように小規模にすることはできます。 詳細については、SQL_MAX_CONCURRENT_ACTIVITIES と SQL_MAX_DRIVER_CONNECTIONS のオプションを参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明、および[ステートメント処理](../../../odbc/reference/develop-app/statement-handles.md)と[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)です。
