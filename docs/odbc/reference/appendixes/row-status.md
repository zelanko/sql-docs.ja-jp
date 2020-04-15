---
title: 行の状態 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4ae4169dc3f2a491663f4a86c564cfee5c2f4d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305101"
---
# <a name="row-status"></a>行の状態
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは、行の状態のバッファーをキャッシュに作成します。 カーソル ライブラリは、このバッファーから行状態配列 (SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定) の値を取得します。 カーソル ライブラリは、行ごとにこのバッファを次の値に設定します。  
  
-   SQL_ROW_DELETED行に位置指定された削除ステートメントを実行するとき。  
  
-   **SQL_ROW_ERROR SQLFetch**を使用してデータ ソースから行を取得中にエラーが発生したときに発生します。  
  
-   **sqlFetch**を使用してデータ ソースから行を正常にフェッチした場合にSQL_ROW_SUCCESSします。  
  
-   SQL_ROW_UPDATED行に位置指定された update ステートメントを実行するときに使用します。
