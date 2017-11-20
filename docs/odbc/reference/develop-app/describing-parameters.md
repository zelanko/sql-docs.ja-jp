---
title: "パラメーターを記述する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d78b3b7ac10fae37bb35f88cefaf5983e0df09a4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="describing-parameters"></a>パラメーターを記述します。
**SQLBindParameter**パラメーターを記述する引数を持つ: その SQL 型、有効桁数、および小数点以下桁数です。 ドライバーは、この情報を使用または*メタデータ、*パラメーター値をデータ ソースで必要な型に変換します。 一見すると、思えますが、ドライバーが、パラメーターのメタデータをアプリケーション、つまりより認識する最適な位置にあります。結局のところ、結果セットの列、ドライバーは、メタデータを検出簡単にできます。 結局のところ、大文字と小文字ではありません。 最初に、ほとんどのデータ ソースは用意されていない、ドライバーがパラメーターのメタデータを検出するためです。 2 つ目は、ほとんどのアプリケーションが既にわかっているメタデータ。  
  
 SQL ステートメントが、アプリケーションでハード コードされた場合は、アプリケーションの作成者は既に各パラメーターの型を認識します。 SQL ステートメントが実行時にアプリケーションによって構築される場合、アプリケーションは、ステートメントを作成するメタデータを特定できます。 たとえば、アプリケーションが、句を構築とき  
  
```  
WHERE OrderID = ?  
```  
  
 呼び出すことができます**SQLColumns** OrderID 列にします。  
  
 アプリケーション容易に判別できなくパラメーターのメタデータのみの状況、ユーザーがパラメーター化されたステートメントを入力したときです。 この場合、アプリケーションが呼び出す**SQLPrepare** 、ステートメントを準備**SQLNumParams** 、パラメーターの数を決定するおよび**SQLDescribeParam**を記述するには各パラメーター。 ただし、前述したよう、ほとんどのデータ ソースは用意されていない、したがってパラメーターのメタデータを検出するドライバーを**SQLDescribeParam**広くサポートされていません。

