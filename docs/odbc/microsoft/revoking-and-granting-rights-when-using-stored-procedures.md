---
title: ストアド プロシージャを使用する場合の権限の取り消しと付与 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 469e6f0fdc6794e3bd163844e43821798aa4a617
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303988"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>ストアド プロシージャ使用時の権限の取り消しと付与
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用 Microsoft ODBC ドライバーは、ストアド プロシージャによってアクセスされるテーブルに対してユーザー権限が付与され、取り消されると、次のエラー メッセージを返します。  
  
 SQL_ERROR=-1  
  
 szErrorMsg="[マイクロソフト][オラクルのためのODBCドライバ]パラメータの数が間違っています"  
  
 szErrorMsg="[マイクロソフト][Oracle のための ODBC ドライバー]構文エラーまたはアクセス違反"  
  
 Oracle OCI 関数 Odessp() の呼び出しは、このシナリオでは失敗しますが、デフォルトのパラメータを実装するために必要です。 基になるテーブル権限を変更した後、ストアド プロシージャを再コンパイルしてから、再度実行する必要があります。
