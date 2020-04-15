---
title: 列のバインド |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fca4cfb1455c91ca57f7b1769266e2040d6a3511
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301823"
---
# <a name="binding-columns"></a>バインディング列
データ ソースからフェッチされたデータは、アプリケーションがこの目的のために割り当てた変数でアプリケーションに返されます。 これを行う前に、アプリケーションは、これらの*変数を結果*セットの列に関連付けるかバインドする必要があります。概念的には、このプロセスは、アプリケーション変数をステートメント・パラメーターにバインドするのと同じです。 アプリケーションは、結果セット列に変数をバインドするときに、その変数 (アドレス、データ型など) をドライバーに記述します。 ドライバーは、そのステートメントを保持する構造体にこの情報を格納し、行がフェッチされたときに、列から値を返す情報を使用します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットの列のバインド](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)
