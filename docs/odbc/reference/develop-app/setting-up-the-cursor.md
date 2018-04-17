---
title: カーソルを設定する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39bb6f6f61d8477fae1f0a07b2960b77dd987643
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-the-cursor"></a>カーソルを設定します。
設定の結果を作成するステートメントを実行する前に、アプリケーションは、カーソルの種類を指定できます。 これは、SQL_ATTR_CURSOR_TYPE ステートメント属性を持つ。 アプリケーションが、型を明示的に指定しない場合は、順方向専用カーソルが使用されます。 混合カーソルを表示するには、アプリケーションが、キーセット ドリブン カーソルを指定しますが、結果セットのサイズより小さいキーセットのサイズを宣言しています。  
  
 カーソルのキーセット ドリブン、混合場合、アプリケーションは、キーセットのサイズにも指定できます。 これは、SQL_ATTR_KEYSET_SIZE ステートメント属性を持つ。 キーセットのサイズが既定では、0 に設定されている場合は、キーセットのサイズが結果セットのサイズに設定されているし、キーセット ドリブン カーソルを使用します。 カーソルが開かれた後、キーセットのサイズを変更できます。  
  
 アプリケーションは、行セットのサイズを設定できますも詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)、このセクションで前述しました。
