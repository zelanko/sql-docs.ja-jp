---
title: "カーソルを設定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b442a732eb16b4047eabe9c507eb5cd5d2887a99
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="setting-up-the-cursor"></a>カーソルを設定します。
設定の結果を作成するステートメントを実行する前に、アプリケーションは、カーソルの種類を指定できます。 これは、SQL_ATTR_CURSOR_TYPE ステートメント属性を持つ。 アプリケーションが、型を明示的に指定しない場合は、順方向専用カーソルが使用されます。 混合カーソルを表示するには、アプリケーションが、キーセット ドリブン カーソルを指定しますが、結果セットのサイズより小さいキーセットのサイズを宣言しています。  
  
 カーソルのキーセット ドリブン、混合場合、アプリケーションは、キーセットのサイズにも指定できます。 これは、SQL_ATTR_KEYSET_SIZE ステートメント属性を持つ。 キーセットのサイズが既定では、0 に設定されている場合は、キーセットのサイズが結果セットのサイズに設定されているし、キーセット ドリブン カーソルを使用します。 カーソルが開かれた後、キーセットのサイズを変更できます。  
  
 アプリケーションは、行セットのサイズを設定できますも詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)、このセクションで前述しました。
