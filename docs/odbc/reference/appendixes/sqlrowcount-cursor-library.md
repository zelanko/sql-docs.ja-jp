---
title: SQLRowCount (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a74130031623a1198eada5e2bd62a992867c4e3a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLRowCount**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLRowCount**を参照してください[Sqlrowcount](../../../odbc/reference/syntax/sqlrowcount-function.md)です。  
  
 アプリケーションを呼び出すと**SQLRowCount**ステートメントでは、カーソルに関連付けられている、カーソル ライブラリは、ドライバーから取得したデータの行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**ステートメントでは、位置指定更新または削除ステートメントに関連付けられている、カーソル ライブラリがステートメントによって影響を受ける行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**後、**選択**ステートメントでは、カーソル ライブラリは、-1 を返します。
