---
title: ステートメントオプション |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca40765dff98e9102fbe36e88c7e79535f311d97
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299212"
---
# <a name="statement-options"></a>ステートメントのオプション
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 これらのオプションを使用すると、アプリケーション内で特定の実行ステートメントをカスタマイズできます。  
  
|ステートメントオプション|Notes|  
|----------------------|-----------|  
|SQL_BIND_TYPE|2,147,483,647 バイトまたは使用可能なメモリを超えることはできません。|  
|SQL_CONCURRENCY|許容値については、「カーソルの[種類」および「同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)」を参照してください。|  
|SQL_CURSOR_TYPE|ドライバはSQL_CURSOR_DYNAMICを許可しません。 詳細については[、「SQL セットスクロール オプション](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md)」を参照してください。 許容値については、「カーソルの[種類」および「同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)」を参照してください。|  
|SQL_GET_BOOKMARK|現在のレコード番号のブックマークである 32 ビット整数値を返します。 取得のみ。設定できません。|  
|SQL_KEYSET_SIZE|0 に設定できます。|  
|SQL_MAX_ROWS|結果セットから返される最大行数。|  
|SQL_ROW_NUMBER|結果セット内の現在の行の位置を指定する 32 ビットの整数を返します。 取得のみ。設定できません。|  
|SQL_ROWSET_SIZE|4,294,967,296 行を超えることはできません。ただし、要求を処理するためには、コンピュータに十分な仮想メモリが必要です。|  
|SQL_USE_BOOKMARKS|SQL_USE_BOOKMARKSをSQL_UB_ONに設定し、固定長のブックマークを公開します。|
