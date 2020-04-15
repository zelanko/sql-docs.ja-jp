---
title: インデックス ステートメントを削除する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 638bae6491c020519a0123ff56fe31e9a9ca1cf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303433"
---
# <a name="drop-index-statement"></a>DROP INDEX ステートメント
Access、dBASE、または Paradox ドライバを使用する場合、DROP INDEX ステートメントの構文は "DROP INDEX a on b" で、"a" はインデックスの名前、"b" はテーブルの名前 (DROP INDEX*インデックス名*ではない) です。  
  
 Paradox ドライバを使用すると、DROP INDEX ステートメントによって Paradox セカンダリ インデックス ファイルが削除されます。  
  
 DROP INDEX ステートメントは、Excel またはテキスト ドライバーではサポートされていません。
