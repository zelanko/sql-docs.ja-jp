---
title: '手順 6: は、データ ソースから切断 |Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a42465e763f8f6d520ed9c1dac42612aa1b28575
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802440"
---
# <a name="step-6-disconnect-from-the-data-source"></a>ステップ 6: データ ソースからの切断
最後の手順は、データ ソースから切断するのには次の図に示すようにします。 最初に、アプリケーションが呼び出すことによって任意のステートメント ハンドルを解放**SQLFreeHandle**します。 詳細については、[ステートメント ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)を参照してください。  
  
 ![データ ソースからの切断を示しています](../../../odbc/reference/develop-app/media/pr17.gif "pr17。")  
  
 次に、アプリケーションを持つデータ ソースから切断**SQLDisconnect**し、使用して、接続ハンドルの解放**SQLFreeHandle**します。 詳細については、[データ ソースまたはドライバーからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)を参照してください。  
  
 最後に、アプリケーションが使用して、環境ハンドルを解放**SQLFreeHandle**とドライバー マネージャーをアンロードします。 詳細については、[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)を参照してください。
