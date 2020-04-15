---
title: 記述子のコピー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e2e5897afc3673a21396e256df04d25008c8cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301671"
---
# <a name="copying-descriptors"></a>記述子のコピー
**SQLCopyDesc**関数は、ある記述子のフィールドを別の記述子にコピーするために呼び出されます。 フィールドは、アプリケーション記述子または IPD にのみコピーできますが、IRD にはコピーできません。 フィールドは、任意の型の記述子からコピーできます。 ソース記述子とターゲット記述子の両方に定義されているフィールドのみがコピーされます。 記述子の割り当てタイプは変更できないため **、SQLCopyDesc**はSQL_DESC_ALLOC_TYPEフィールドをコピーしません。 コピーされたフィールドは、既存のフィールドを上書きします。  
  
 あるステートメント・ハンドルの ARD は、別のステートメント・ハンドルの APD として機能します。 これにより、アプリケーションは、アプリケーション レベルでデータをコピーせずに、テーブル間で行をコピーできます。 これを行うには、テーブルのフェッチされた行を記述する行記述子が、INSERT ステートメントのパラメーターのパラメーター記述子として再利用されます。 この操作を正常に実行するには、SQL_MAX_CONCURRENT_ACTIVITIES情報の種類が 1 より大きい必要があります。
