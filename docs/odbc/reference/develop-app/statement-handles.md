---
title: ステートメントハンドル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be90fe10d10a0b087d1c9724fed249805eb4dba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299678"
---
# <a name="statement-handles"></a>ステートメント ハンドル
*ステートメント*は、SELECT FROM ** \* Employee**などの SQL ステートメントとして最も簡単に考えやすい。 ただし、ステートメントは単なる SQL ステートメントではなく、その SQL ステートメントに関連付けられたすべての情報 (ステートメントによって作成された結果セット、ステートメントの実行で使用されるパラメーターなど) で構成されます。 ステートメントには、アプリケーション定義の SQL ステートメントを持つ必要はありません。 たとえば **、SQLTables**などのカタログ関数がステートメントで実行されると、テーブル名のリストを返す定義済み SQL ステートメントが実行されます。  
  
 各ステートメントは、ステートメント・ハンドルによって識別されます。 ステートメントは単一の接続に関連付けられており、その接続には複数のステートメントが存在する可能性があります。 ドライバーによっては、サポートするアクティブなステートメントの数を制限するものもあります。**SQLGetInfo**のSQL_MAX_CONCURRENT_ACTIVITIES オプションは、1 つの接続でドライバーがサポートするアクティブなステートメントの数を指定します。 ステートメントが保留中の結果を持つ場合、結果セット、または**INSERT**、 **UPDATE**、**または DELETE**ステートメントの影響を受ける行の数、または**SQLPutData**への複数の呼び出しを伴うデータの送信時に *、ステートメントがアクティブ*として定義されます。  
  
 ODBC (ドライバー マネージャーまたはドライバー) を実装するコードの一部内で、ステートメント ハンドルは、ステートメント情報を含む構造体を識別します。  
  
-   ステートメントの状態  
  
-   現在のステートメント レベルの診断  
  
-   ステートメントのパラメーターおよび結果セット列にバインドされたアプリケーション変数のアドレス  
  
-   各ステートメント属性の現在の設定  
  
 ステートメント ハンドルは、ほとんどの ODBC 関数で使用されます。 特に、パラメーターと結果セット列 **(SQLBindParameter**および**SQLBindCol)** をバインドする関数で使用され、ステートメント **(SQLPrepare、SQLExecute、** および**SQLExecDirect)** を準備および実行し、メタデータ **(SQLColAttribute**および**SQLDescribeCol)** を取得し、結果を取得します (**SQLFetch**) 診断を取得します (**SQLGetDiagField**および**SQLGetDiagRec**)。 **SQLExecute** また、カタログ関数 (**SQLColumns**、 **SQLTables**など ) や他の多くの関数でも使用されます。  
  
 ステートメント ハンドルは **、SQLAllocHandle**で割り当てられ **、SQLFreeHandle**で解放されます。
