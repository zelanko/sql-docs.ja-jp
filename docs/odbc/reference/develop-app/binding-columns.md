---
title: "列をバインド |Microsoft ドキュメント"
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5903070b8918baa9734e5d188d90861322b57986
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns"></a>列のバインド
この目的のため、アプリケーションが割り当てられている変数のアプリケーションには、データ ソースからフェッチされたデータが返されます。 これを行うことができます、前に、アプリケーションに関連付ける必要があります、または*バインド*結果の列にこれらの変数の設定。 概念的には、このプロセスは、ステートメントのパラメーターをアプリケーション変数のバインドと同じです。 アプリケーションにバインドする変数と、結果セット列、その変数がについて説明します-アドレスやデータ型: ドライバーにします。 ドライバーでは、そのステートメントを保持し、情報を使用して、行がフェッチしたときに、列から値を返す、構造のこの情報を格納します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [バインドの結果セットの列](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)
