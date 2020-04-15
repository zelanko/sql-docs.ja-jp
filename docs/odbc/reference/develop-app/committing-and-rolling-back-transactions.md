---
title: トランザクションのコミットとロールバック |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c272d60242d31622452c4dcb0f6a16c4838768f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299112"
---
# <a name="committing-and-rolling-back-transactions"></a>トランザクションのコミットとロールバック
手動コミット モードでトランザクションをコミットまたはロールバックするには、アプリケーションが**SQLEndTran**を呼び出します。 トランザクションをサポートする Dbms のドライバーは、通常 **、COMMIT**または**ROLLBACK**ステートメントを実行することによってこの関数を実装します。 ドライバ マネージャは、接続が自動コミット モードの場合は**SQLEndTran**を呼び出しません。アプリケーションがトランザクションをロールバックしようとしても、単にSQL_SUCCESSを返します。 トランザクションをサポートしない DBMS のドライバーは常に自動コミット モードであるため、何もせずにSQL_SUCCESSを返す**SQLEndTran**を実装するか、まったく実装しないかのどちらかです。  
  
> [!NOTE]  
>  **アプリケーションは、SQLExecute**または**SQLExecDirect**を使用して**COMMIT**ステートメントまたは**ROLLBACK**ステートメントを実行してトランザクションをコミットまたはロールバックしないでください。 これを行った場合の影響は未定義です。 可能性のある問題には、トランザクションがいつアクティブであるかがドライバでわからなくなり、トランザクションをサポートしていないデータ ソースに対してこれらのステートメントが失敗する可能性があります。 これらのアプリケーションは、代わりに**SQLEndTran を**呼び出す必要があります。  
  
 アプリケーションが**SQLEndTran**に環境ハンドルを渡すが、接続ハンドルを渡さない場合、ドライバー マネージャーは概念的に環境内の 1 つまたは複数のアクティブな接続を持つ各ドライバーの環境ハンドルを**SQLEndTran**を呼び出します。 ドライバーは、環境内の各接続でトランザクションをコミットします。 ただし、ドライバーとドライバー マネージャーは、環境内の接続に対して 2 フェーズ コミットを実行する、どちらも注意してください。これは、環境内のすべての接続に対して**SQLEndTran**を同時に呼び出すプログラミングの便宜に過ぎません。  
  
 (2*フェーズ コミット*は、一般に複数のデータ ソースに分散されたトランザクションをコミットするために使用されます。 最初のフェーズでは、データ ソースがトランザクションの一部をコミットできるかどうかについてポーリングされます。 第 2 段階では、トランザクションは実際にすべてのデータ ソースでコミットされます。 最初のフェーズでトランザクションをコミットできないデータ ソースが応答した場合、第 2 フェーズは発生しません)。
