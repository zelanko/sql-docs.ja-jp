---
title: 列のバインド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106216"
---
# <a name="binding-columns"></a>バインディング列
データソースからフェッチされたデータは、アプリケーションによってこの目的で割り当てられた変数でアプリケーションに返されます。 これを行うには、アプリケーションがこれらの変数を結果セットの列に関連付けるか、または*バインド*する必要があります。概念的には、このプロセスは、ステートメントパラメーターへのアプリケーション変数のバインドと同じです。 アプリケーションが変数を結果セット列にバインドすると、その変数アドレス、データ型などがドライバーに対して記述されます。 ドライバーは、この情報をそのステートメント用に保持する構造体に格納し、その情報を使用して、行がフェッチされるときに列から値を返します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットの列のバインド](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)
