---
title: "SQLGetDescField と SQLGetDescRec (カーソル ライブラリ) |Microsoft ドキュメント"
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
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff32edcc14799980c1d8ec9e05bd27456d71a132
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField と SQLGetDescRec (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでの使用について説明します、 **SQLGetDescField**と**SQLGetDescRec**カーソル ライブラリ内の関数。 これらの関数の概要については、次を参照してください。 [SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)と[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)です。  
  
 カーソル ライブラリ実行**SQLGetDescRec**ブックマーク列のメタデータを返します。 カーソル ライブラリを実行**SQLGetDescField**によって返される同じフィールドを返す**SQLGetDescRec**、これは、SQL_DESC_NAME、SQL_DESC_TYPE、SQL_DESC_DATETIME_INTERVAL_CODE、SQL_DESC_OCTET_長さ、SQL_DESC_PRECISION、SQL_DESC_SCALE、および SQL_DESC_NULLABLE です。 整合性、 **SQLGetDescField**も SQL_DESC_UNNAMED が返されます。  
  
 カーソル ライブラリ実行**SQLGetDescField**ブックマーク列をバインドするために設定されている、次の値フィールドを返すに呼び出されたとき: SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、およびSQL_DESC_LENGTH です。  
  
 カーソル ライブラリ実行**SQLGetDescField** SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE、または SQL_DESC_ROW_STATUS_PTR フィールドの値を返す呼び出されたとき。 これらのフィールドは、ブックマークの行だけでなく、任意の行に対して返されますことができます。  
  
 アプリケーションを呼び出す場合**SQLGetDescField**カーソル ライブラリがドライバーへの呼び出しを渡すに記載されているもの以外の任意のフィールドの値を取得します。

