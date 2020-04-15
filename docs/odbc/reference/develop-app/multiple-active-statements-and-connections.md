---
title: 複数のアクティブなステートメントと接続 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302431"
---
# <a name="multiple-active-statements-and-connections"></a>複数のアクティブなステートメントと接続
一部のドライバーおよび DBMS では、一度にアクティブにできるステートメントと接続の数が制限されます。 これらの数値は 1 つにも小さくすることができます。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明の SQL_MAX_CONCURRENT_ACTIVITIES およびSQL_MAX_DRIVER_CONNECTIONSオプション、および[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)と[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)を参照してください。
