---
title: ストアド プロシージャの使用時に権限の付与と取り消し |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e881201e4653a168faff2fa438be19c1ca37e9b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127961"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>ストアド プロシージャ使用時の権限の取り消しと付与
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft ODBC Driver for Oracle では、ユーザー権限の付与し、ストアド プロシージャがアクセスするテーブルで、取り消すときに、次のエラー メッセージが返されます。  
  
 SQL_ERROR = 1  
  
 後"[Microsoft] [ODBC driver for Oracle] 間違った数のパラメーター"を =  
  
 後 =「[Microsoft] [ODBC driver for Oracle] 構文エラーまたはアクセス違反です」  
  
 Oracle OCI 関数 Odessp() への呼び出しがこのシナリオでは失敗が既定のパラメーターを実装するために必要です。 基になるテーブルのアクセス許可を変更した後に、もう一度実行する前に、ストアド プロシージャが再コンパイルする必要があります。
