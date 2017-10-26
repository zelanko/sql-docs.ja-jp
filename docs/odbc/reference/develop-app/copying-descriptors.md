---
title: "記述子のコピー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8cd2ea29713d3bf1e05e76de21397f71dd30c824
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="copying-descriptors"></a>記述子のコピー
**SQLCopyDesc**記述子が 1 つのフィールドを別の記述子にコピーする関数が呼び出されます。 フィールドは、IRD ではなく、アプリケーション記述子または、IPD にのみコピーできます。 フィールドは、任意の型記述子からコピーすることができます。 ソースとターゲットの両方の記述子に対して定義されているフィールドだけがコピーされます。 **SQLCopyDesc**記述子の割り当ての種類を変更できないため、SQL_DESC_ALLOC_TYPE フィールドはコピーされません。 コピーしたフィールドは、既存のフィールドを上書きします。  
  
 1 つのステートメント ハンドルで、ARD は、別のステートメント ハンドルで APD として使用できます。 これにより、アプリケーション、アプリケーション レベルでデータをコピーしないでテーブル間の行をコピーします。 これを行うには、テーブルのフェッチされた行が示す行記述子は、INSERT ステートメントのパラメーターのパラメーターの記述子として再利用します。 SQL_MAX_CONCURRENT_ACTIVITIES 情報の種類は、この操作が成功する場合は 1 より大きくなければなりません。

