---
title: "ストアド プロシージャを無効にしを使用する場合は、権限を付与する |Microsoft ドキュメント"
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 67bad57e201d10c5eb29aafb19fa9f513c43b172
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>ストアド プロシージャを取り消し、付与する権限を使用する場合
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft ODBC Driver for Oracle では、ユーザー権利の付与し、ストアド プロシージャからアクセスするテーブルに対して、失効したときに、次のエラー メッセージが返されます。  
  
 SQL_ERROR = 1  
  
 後 ="[Microsoft] [ODBC driver for Oracle] 間違った数のパラメーター"  
  
 後 =「[Microsoft] [ODBC driver for Oracle] 構文エラーまたはアクセス違反」  
  
 Odessp() Oracle OCI 関数への呼び出しを実行するが、このシナリオではできずは既定のパラメーターを実装するために必要です。 基になるテーブルのアクセス許可が変更されると、後にもう一度実行する前に、ストアド プロシージャを再コンパイルする必要があります。
