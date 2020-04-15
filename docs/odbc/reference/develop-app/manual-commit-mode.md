---
title: 手動コミット モード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a00ff373e374d0940b3e7259eeb01e26b620cae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287876"
---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミット モードでは、アプリケーションは* **SQLEndTran**を呼び出してトランザクションをコミットするか、ロールバックすることによって、明示的にトランザクションを完了する必要があります。 これは、ほとんどのリレーショナル・データベースの通常のトランザクション・モードです。  
  
 ODBC のトランザクションは、明示的に開始する必要はありません。 代わりに、アプリケーションがデータベースで操作を開始するたびに、トランザクションが暗黙的に開始されます。 データ ソースが明示的なトランザクションの開始を必要とする場合、アプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションがない場合は、必ず、ドライバーがデータ ソースを提供する必要があります。
