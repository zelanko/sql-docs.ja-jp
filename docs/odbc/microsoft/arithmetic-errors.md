---
title: "算術エラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d3585f6e1be7a3f9451231004979321202d7852
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="arithmetic-errors"></a>算術エラー
ODBC ドライバーは、各の行をフェッチと SELECT ステートメントの WHERE 句を評価します。 行には、0 除算、または数値のオーバーフローなどの算術エラーが発生した値が含まれている場合、ドライバーは、すべての行を返しますが、算術エラーのある列のエラーを返します。 挿入または更新する、ただし、ODBC ドライバーを挿入する、または停止が最初の算術エラーが発生したときにデータを更新します。

