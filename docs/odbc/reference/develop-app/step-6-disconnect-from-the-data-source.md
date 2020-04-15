---
title: '手順 6: データ ソースから切断する |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df8cd94435d74bf813b0b64be0753a0beb44d354
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302793"
---
# <a name="step-6-disconnect-from-the-data-source"></a>手順 6:データ ソースから切断する
最後の手順では、次の図に示すように、データ ソースから切断します。 まず、アプリケーションは**SQLFreeHandle**を呼び出すことによって、すべてのステートメント ハンドルを解放します。 詳細については、「ステートメント[ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)」を参照してください。  
  
 ![データ ソースからの切断の表示](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 次に、アプリケーションは**SQLDisconnect**を使用してデータ ソースから切断し、接続ハンドルを**解放**します。 詳細については、「[データ ソースまたはドライバからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)」を参照してください。  
  
 最後に、アプリケーションは **、SQLFreeHandle**を使用して環境ハンドルを解放し、ドライバー マネージャーをアンロードします。 詳細については、「[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)」を参照してください。
