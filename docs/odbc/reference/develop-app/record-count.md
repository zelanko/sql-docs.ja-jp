---
title: レコード カウント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f8b0a6fc7aa5765d9373af33ab4fac0a4a07aac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610432"
---
# <a name="record-count"></a>レコード カウント
記述子の SQL_DESC_COUNT ヘッダー フィールドは、データを格納する番号が最大のレコードの 1 から始まるインデックスです。 このフィールドは、すべての列またはバインドされているパラメーターの数ではありません。 記述子が割り当てられると、SQL_DESC_COUNT の初期値は 0 です。  
  
 ドライバーは、割り当てし、記述子の情報を保持するために必要な任意の記憶域の管理に必要なすべてのアクションを実行します。 アプリケーションが、明示的に、記述子のサイズを指定したりする新しいレコードを割り当てます。 アプリケーションでは、その数は SQL_DESC_COUNT の値よりも大きい記述子レコードの情報を提供するときに、ドライバーは SQL_DESC_COUNT を自動的に増加します。 アプリケーションでは、番号が最大の記述子レコードがバインド解除、ドライバーは最高の残りのバインドされたレコードの数を格納する SQL_DESC_COUNT を自動的に減少します。
