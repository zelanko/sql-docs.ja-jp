---
title: SQL ステートメントのバッチの処理 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], batches
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], batches
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- SQL statements [ODBC], batches
- batches [ODBC], processing batches of SQL statements
ms.assetid: 04b93ef9-11de-47a3-8bd8-ba963c42f182
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec0e4b67d75b1ff1b14eb11682869041717a4055
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81308033"
---
# <a name="processing-batches-of-sql-statements"></a>SQL ステートメントのバッチ処理
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソルライブラリでは、SQL ステートメントのバッチがサポートされていません。このステートメントには、SQL_ATTR_PARAMSET_SIZE statement 属性が1より大きい SQL ステートメントが含まれます。 アプリケーションが SQL ステートメントのバッチをカーソルライブラリに送信した場合、結果は未定義になります。
