---
title: SQLGet データ (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07200d48f439c97003da7062fc218cd2f3081d1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307843"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLGetData**関数の使用について説明します。 **SQLGetData**の一般的な情報については、「 [SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)」を参照してください。  
  
 カーソル ライブラリは、まず、現在の行のバインドされた各列のキャッシュに格納されている値を列挙する**WHERE**句を使用して**SELECT**ステートメントを構築することにより **、SQLGetData**を実装します。 次に **、SELECT**ステートメントを実行して行を再選択し、ドライバーの**SQLGetData**を呼び出して、データ ソースからデータを取得します (キャッシュとは対照的)。  
  
> [!CAUTION]  
>  現在の行を識別するためにカーソル ライブラリによって作成された**WHERE**句は、行の識別、別の行の識別、または複数行の識別に失敗する可能性があります。 詳細については、「[検索ステートメントの作成](../../../odbc/reference/appendixes/constructing-searched-statements.md)」を参照してください。  
  
 SQL_ATTR_USE_BOOKMARKSステートメント属性が SQL_UB_VARIABLE に設定されている場合 **、SQLGetData**を列 0 で呼び出してブックマーク データを返すことができます。  
  
 **SQLGetData**の呼び出しには、次の制限が適用されます。  
  
-   前方専用カーソルに対して**SQLGetData**を呼び出すことはできません。  
  
-   **SQLGetData**は、次の条件が満たされている場合にのみ**SELECT**呼び出すことができます。**SELECT**ステートメントに、結合 **、UNION**句、または GROUP **BY**句が含まれていませんでした。選択リストでエイリアスまたは式を使用する列は**SQLBindCol**でバインドされていません。  
  
-   ドライバーが 1 つのアクティブ ステートメントのみをサポートしている場合、カーソル ライブラリは **、SELECT**ステートメントを実行して**SQLGetData**を呼び出す前に、結果セットの残りの部分をフェッチします。
