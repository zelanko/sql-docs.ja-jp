---
title: レコード数 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28e503ae4602d87fc9138ed018ee1e95f135ec57
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281818"
---
# <a name="record-count"></a>レコード カウント
記述子のSQL_DESC_COUNTヘッダー フィールドは、データを含む最も番号の大きいレコードの 1 から始まるインデックスです。 このフィールドは、バインドされているすべての列またはパラメーターのカウントではありません。 記述子が割り当てられると、SQL_DESC_COUNTの初期値は 0 になります。  
  
 ドライバーは、記述子情報を保持するために必要なストレージを割り当て、維持するために必要なアクションを実行します。 アプリケーションは、記述子のサイズを明示的に指定したり、新しいレコードを割り当てたりしません。 アプリケーションが、SQL_DESC_COUNTの値よりも大きい数の記述子レコードの情報を提供すると、ドライバーは自動的にSQL_DESC_COUNTを増加します。 アプリケーションが最も番号の大きい記述子レコードをアンバインドすると、ドライバーは自動的にSQL_DESC_COUNTを減少し、残りの最大のバインド レコードの数を含めます。
