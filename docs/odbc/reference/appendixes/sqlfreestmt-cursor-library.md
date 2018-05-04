---
title: SQLFreeStmt (カーソル ライブラリ) |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cd1e2eef830ef36887f488dcd6f6c0f4aac0483
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLFreeStmt**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLFreeStmt**を参照してください[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)です。  
  
 アプリケーションを呼び出す場合**SQLFreeStmt** SQL_UNBIND オプションを呼び出した後**SQLExtendedFetch**、 **SQLFetch**、または**SQLFetchScroll**、カーソル ライブラリには、エラーが返されます。 結果セットの列をバインド解除できますが、前に、アプリケーションを呼び出す必要があります**SQLCloseCursor**または**SQLFreeStmt** SQL_CLOSE オプションを使用します。
