---
title: 複数のアクティブなステートメントと接続 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76b74ff748a62a401955e4ea4a995f507314124e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942825"
---
# <a name="multiple-active-statements-and-connections"></a>複数のアクティブなステートメントと接続
一部のドライバーおよび Dbms では、同時にアクティブにできるステートメントと接続の数が制限されています。 これらの数値は、1つだけ小さくすることができます。 詳細については、「 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明」の SQL_MAX_CONCURRENT_ACTIVITIES と SQL_MAX_DRIVER_CONNECTIONS のオプションと、[ステートメントハンドル](../../../odbc/reference/develop-app/statement-handles.md)および[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)を参照してください。
