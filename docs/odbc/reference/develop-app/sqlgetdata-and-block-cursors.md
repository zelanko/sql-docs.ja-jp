---
title: カーソルをブロックする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b60d7093552b8f1dbed87d9ad8840ddb5a9e0799
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299752"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData およびブロック カーソル
**SQLGetData**は、1 つの行の単一列を操作し、複数の行からデータを含む配列をフェッチすることはできません。 これは **、SQLGetData**の主な用途は、長いデータを一部でフェッチするものであり、一度に複数の行に対してこれを行う理由がほとんどまたはまったくないためです。  
  
 ブロック カーソルで**SQLGetData**を使用するには、アプリケーションは最初に**SQLSetPos**を呼び出してカーソルを 1 行に配置します。 その後、その行の列に対して**SQLGetData**を呼び出します。 ただし、この動作はオプションです。 ドライバーがブロック カーソルを使用して**SQLGetData**の使用をサポートするかどうかを確認するには、アプリケーションは、SQL_GETDATA_EXTENSIONS オプションを使用して**SQLGetInfo**を呼び出します。
