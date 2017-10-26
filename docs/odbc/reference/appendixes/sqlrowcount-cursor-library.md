---
title: "SQLRowCount (カーソル ライブラリ) |Microsoft ドキュメント"
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9460f4f4bbc522fc421b7e40b261fe17a8410a09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLRowCount**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLRowCount**を参照してください[Sqlrowcount](../../../odbc/reference/syntax/sqlrowcount-function.md)です。  
  
 アプリケーションを呼び出すと**SQLRowCount**ステートメントでは、カーソルに関連付けられている、カーソル ライブラリは、ドライバーから取得したデータの行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**ステートメントでは、位置指定更新または削除ステートメントに関連付けられている、カーソル ライブラリがステートメントによって影響を受ける行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**後、**選択**ステートメントでは、カーソル ライブラリは、-1 を返します。

