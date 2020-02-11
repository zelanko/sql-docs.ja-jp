---
title: レコード数 |Microsoft Docs
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
ms.openlocfilehash: d4d684fb6d9614defdca3897c53c4bae9fc231a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138083"
---
# <a name="record-count"></a>レコード カウント
記述子の SQL_DESC_COUNT header フィールドは、データを格納する最大番号のレコードの1から始まるインデックスです。 このフィールドは、バインドされているすべての列またはパラメーターの数ではありません。 記述子が割り当てられると、SQL_DESC_COUNT の初期値は0になります。  
  
 ドライバーは、記述子情報を保持するために必要なすべてのストレージを割り当て、維持するために必要なアクションを実行します。 アプリケーションでは、記述子のサイズを明示的に指定したり、新しいレコードを割り当てたりすることはありません。 数値が SQL_DESC_COUNT の値よりも大きい記述子レコードの情報がアプリケーションによって提供されると、ドライバーは自動的に SQL_DESC_COUNT を増やします。 アプリケーションが一番大きい番号の記述子レコードをバインド解除すると、ドライバーは、残りの最大のレコード数を含むように、SQL_DESC_COUNT を自動的に減らします。
