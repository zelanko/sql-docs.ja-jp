---
title: 識別子の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7154f2db09b69e6376b1fe3af1de3f2c646ee94e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286252"
---
# <a name="identifiers-limitations"></a>識別子の制限事項
識別子にスペースまたは特殊記号が含まれている場合、その識別子は引用符で囲む必要があります。 有効な名前は 64 文字以内の文字列で、最初の文字はスペースであってはならない。 有効な名前には、制御文字または次の特殊文字を含めることはできません &#124;。 [ ] . ! $ .  
  
 *ODBC プログラマ リファレンス*の付録 C の SQL 文法に記載されている予約語 (または予約語の省略形) を識別子 (つまり、テーブル名または列名) として使用しないでください。
