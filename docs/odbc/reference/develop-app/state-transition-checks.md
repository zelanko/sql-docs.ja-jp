---
title: 状態の移行チェック |Microsoft ドキュメント
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23f2b87fc943535075e1456bb31366ff9667b07b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="state-transition-checks"></a>状態遷移のチェック
ドライバー マネージャーは、環境、接続、またはステートメントの状態が呼び出される関数に適していることを確認します。 たとえば、接続が、割り当て済みにあります。 状態に**SQLConnect**が呼び出されます。 ステートメントが準備済みである必要があります状態に**SQLExecute**と呼びます。 ドライバー マネージャーは、状態遷移のエラーの SQL_ERROR を返します。
