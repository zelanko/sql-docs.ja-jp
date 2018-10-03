---
title: SQLFreeStmt (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07d56e9b77c7e7e34b0de98ef5704b26aa2b86dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854790"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLFreeStmt**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLFreeStmt**を参照してください[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)します。  
  
 アプリケーションを呼び出す場合**SQLFreeStmt** SQL_UNBIND オプションを呼び出した後**SQLExtendedFetch**、 **SQLFetch**、または**SQLFetchScroll**、カーソル ライブラリ エラーが返されます。 結果セットの列をバインド解除できますが、前に、アプリケーションを呼び出す必要があります**SQLCloseCursor**または**SQLFreeStmt** SQL_CLOSE オプションを使用します。
