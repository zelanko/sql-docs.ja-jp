---
title: パラメーターの説明 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d32e5212ba1ba28262d871498f2974485d38233
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040021"
---
# <a name="describing-parameters"></a>パラメーターの記述
**SQLBindParameter**には、パラメーター (SQL の型、有効桁数、および小数点以下桁数) を記述する引数があります。 ドライバーは、この情報 (または*メタデータ)* を使用して、パラメーター値をデータソースに必要な型に変換します。 一見すると、ドライバーがアプリケーションよりもパラメーターメタデータを認識しやすい位置にあるように見えるかもしれません。結局のところ、ドライバーは結果セット列のメタデータを簡単に検出できます。 結局のところ、そうではありません。 まず、ほとんどのデータソースでは、ドライバーがパラメーターのメタデータを検出する方法が提供されていません。 次に、ほとんどのアプリケーションは既にメタデータを認識しています。  
  
 アプリケーションで SQL ステートメントがハードコーディングされている場合、アプリケーションライターは、各パラメーターの型を既に認識しています。 実行時にアプリケーションによって SQL ステートメントが構築される場合、アプリケーションはステートメントを作成するときにメタデータを判断できます。 たとえば、アプリケーションが句を構築する場合などです。  
  
```  
WHERE OrderID = ?  
```  
  
 ここでは、OrderID 列の**Sqlcolumns**を呼び出すことができます。  
  
 パラメーター化されたステートメントをユーザーが入力したときに、アプリケーションがパラメーターのメタデータを簡単に判断できない場合は、 この場合、アプリケーションは**SQLPrepare**を呼び出して、ステートメントを準備し、パラメーターの数を決定する**sqlnumparams**と、各パラメーターを記述する**SQLDescribeParam**を呼び出します。 ただし、前述のように、ほとんどのデータソースでは、ドライバーがパラメーターメタデータを検出する方法が提供されていないため、 **SQLDescribeParam**は広くサポートされていません。
