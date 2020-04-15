---
title: 算術エラー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299902"
---
# <a name="arithmetic-errors"></a>算術エラー
ODBC ドライバーは、SELECT ステートメントの WHERE 句を評価し、各行をフェッチします。 行に、0 除算や数値オーバーフローなどの算術エラーを引き起こす値が含まれている場合、ドライバーはすべての行を返しますが、算術エラーのある列のエラーを返します。 ただし、挿入または更新時に、最初の算術エラーが発生すると、ODBC ドライバーはデータの挿入または更新を停止します。
