---
title: カーソルの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805d8076c853513d86f9a3a92d9342d1224226c9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299802"
---
# <a name="setting-up-the-cursor"></a>カーソルの設定
アプリケーションは、結果セットを作成するステートメントを実行する前にカーソルの種類を指定できます。 これは、SQL_ATTR_CURSOR_TYPEステートメント属性を使用して行われます。 アプリケーションが型を明示的に指定しない場合は、前方専用カーソルが使用されます。 混合カーソルを取得するには、アプリケーションはキーセット ドリブン カーソルを指定しますが、結果セットサイズよりも小さいキーセット サイズを宣言します。  
  
 キーセットドリブン カーソルと混合カーソルの場合、アプリケーションはキーセットサイズを指定することもできます。 これは、SQL_ATTR_KEYSET_SIZEステートメント属性を使用して行われます。 キーセットサイズが 0 (デフォルト) に設定されている場合、キーセットサイズは結果セットのサイズに設定され、キーセットドリブンカーソルが使用されます。 キーセットのサイズは、カーソルがオープンされた後に変更できます。  
  
 アプリケーションは行セットのサイズを設定することもできます。詳細については、このセクションの前半の「[ブロック カーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)」を参照してください。
