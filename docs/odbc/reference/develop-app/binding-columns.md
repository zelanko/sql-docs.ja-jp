---
title: 列の連結 |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 88e3593276851b6ab38fde0472a70be31b7cbf34
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531872"
---
# <a name="binding-columns"></a>バインディング列
これによって、アプリケーションに割り当てられた変数内のアプリケーションには、データ ソースからフェッチされるデータが返されます。 これを行うことができます、前に、アプリケーションに関連付ける必要があります、または*バインド*結果の列にこれらの変数の設定は、概念的には、このプロセスは、ステートメントのパラメーターをアプリケーション変数のバインドと同じです。 アプリケーションでは、変数が結果セット列にバインドした場合は、ドライバーにその変数のアドレスやデータの種類 - がについて説明します。 ドライバーでは、そのステートメントを保持し、情報を使用して、行をフェッチしたときに、列から値を返す構造体のこの情報を格納します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットの列のバインド](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)
