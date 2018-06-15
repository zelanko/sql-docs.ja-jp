---
title: 算術エラー |Microsoft ドキュメント
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
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 867de0b8982b22f9f9574c334226bccc01798065
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899497"
---
# <a name="arithmetic-errors"></a>算術エラー
ODBC ドライバーは、各の行をフェッチと SELECT ステートメントの WHERE 句を評価します。 行には、0 除算、または数値のオーバーフローなどの算術エラーが発生した値が含まれている場合、ドライバーは、すべての行を返しますが、算術エラーのある列のエラーを返します。 挿入または更新する、ただし、ODBC ドライバーを挿入する、または停止が最初の算術エラーが発生したときにデータを更新します。
