---
title: ステートメントのオプション |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bf99aace8b058e429898846466294cc42612070
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948833"
---
# <a name="statement-options"></a>ステートメントのオプション
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 これらのオプションを使用すると、アプリケーション内の特定の実行ステートメントをカスタマイズできます。  
  
|Statement オプション|メモ|  
|----------------------|-----------|  
|SQL_BIND_TYPE|2147483647バイトまたは使用可能なメモリを超えることはできません。|  
|SQL_CONCURRENCY|使用できる値については、「[カーソルの種類と同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)」を参照してください。|  
|SQL_CURSOR_TYPE|ドライバーで SQL_CURSOR_DYNAMIC が許可されていません。 詳細については、「 [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) 」を参照してください。 使用できる値については、「[カーソルの種類と同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)」を参照してください。|  
|SQL_GET_BOOKMARK|現在のレコード番号のブックマークである32ビット整数値を返します。 Get のみ。を設定できません。|  
|SQL_KEYSET_SIZE|0のみに設定できます。|  
|SQL_MAX_ROWS|結果セットから返される行の最大数。|  
|SQL_ROW_NUMBER|結果セット内の現在の行の位置を指定する32ビット整数を返します。 Get のみ。を設定できません。|  
|SQL_ROWSET_SIZE|4294967296行を超えることはできません。ただし、要求を処理するには、コンピューターに十分な仮想メモリが必要です。|  
|SQL_USE_BOOKMARKS|SQL_UB_ON に SQL_USE_BOOKMARKS を設定し、固定長のブックマークを公開することをサポートしています。|
