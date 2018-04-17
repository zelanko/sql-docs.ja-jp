---
title: SQLBindParameter (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54ee24f29d425bd24788d005fa8ad8a09d781a28
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLBindParameter**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLBindParameter**を参照してください[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)です。  
  
 アプリケーションが呼び出すことができます**SQLBindParameter** C データ型、列のサイズ、およびバインドされた列の 10 進数字の同じ残っている限り、パラメーターを再バインドします。  
  
 カーソル ライブラリでは、バインドのオフセットを使用する SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定をサポートします。 (**SQLBindParameter**この再バインドが発生するに呼び出せる必要はありません)。  
  
 カーソル ライブラリは、実行時データ パラメーターのバインドをサポートします。
