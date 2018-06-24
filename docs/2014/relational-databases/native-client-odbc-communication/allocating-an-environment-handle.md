---
title: 環境ハンドルの割り当て |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89bf5353b37858c12212eed4567e0bae7f49d77f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075518"
---
# <a name="allocating-an-environment-handle"></a>環境ハンドルの割り当て
  どの ODBC 関数をアプリケーションから呼び出す場合でも、呼び出す前に ODBC 環境を初期化して環境ハンドルを割り当てる必要があります。 環境ハンドルはグローバルなコンテキスト ハンドルで、ODBC の他のハンドルのプレースホルダーです。 呼び出すことによって、これを行う**SQLAllocHandle**で、 *HandleType*パラメーターを sql_handle_env として設定し、 *InputHandle* SQL_NULL_HANDLE に設定します。  
  
 環境ハンドルを割り当てたら、使用する ODBC 関数呼び出しのバージョンを指定する環境属性を設定する必要があります。 ODBC 3 を使用します。*x*関数を呼び出す[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)で、*属性*パラメーターまたに設定し、 *ValuePtr* SQL_OV_ に設定ODBC3 です。  
  
## <a name="see-also"></a>参照  
 [SQL Server との通信&#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  