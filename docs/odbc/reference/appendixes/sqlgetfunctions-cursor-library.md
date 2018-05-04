---
title: SQLGetFunctions (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45778aeb876b50e44323f91a0aaf00d480130456
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLGetFunctions**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLGetFunctions**を参照してください[SQLGetFunctions 関数](../../../odbc/reference/syntax/sqlgetfunctions-function.md)です。  
  
 呼び出すと**SQLGetFunctions**、カーソル ライブラリをサポートしていることを返します**SQLExtendedFetch**、 **SQLFetchScroll**、 **SQLSetPos**、および**SQLSetScrollOptions**、だけでなく、ドライバーによってサポートされる関数。
