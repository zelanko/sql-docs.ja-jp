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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302431"
---
# <a name="multiple-active-statements-and-connections"></a>複数のアクティブなステートメントと接続
一部のドライバーおよび Dbms では、同時にアクティブにできるステートメントと接続の数が制限されています。 これらの数値は、1つだけ小さくすることができます。 詳細については、「 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明」の SQL_MAX_CONCURRENT_ACTIVITIES と SQL_MAX_DRIVER_CONNECTIONS のオプションと、[ステートメントハンドル](../../../odbc/reference/develop-app/statement-handles.md)および[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)を参照してください。
