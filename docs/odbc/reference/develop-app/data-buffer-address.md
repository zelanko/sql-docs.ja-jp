---
title: データ バッファーのアドレス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f07f835361fcf29143376fe468a55f0bf26e31e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471131"
---
# <a name="data-buffer-address"></a>データ バッファーのアドレス
アプリケーションでは、データ バッファーのアドレスを渡すという名前の多くの場合、引数にドライバー *ValuePtr*または類似する名前。 呼び出す次の場合など**SQLBindCol**、アプリケーションのアドレスを指定する、*日付*変数。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 説明したように、[割り当ておよび解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  セクションで、遅延のバッファーのアドレスする必要がありますまで有効なバッファーのバインドがありません。  
  
 具体的には禁止されている場合を除き、データ バッファーのアドレスは、null ポインターを指定できます。 ドライバーにデータを送信するために使用するバッファー、これにより、バッファーに通常含まれる情報を無視するドライバーです。 ドライバーからデータを取得するため、バッファーのこれにより、値を返しません。 どちらの場合は、ドライバーは、対応するデータ バッファー長の引数を無視します。
