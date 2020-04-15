---
title: 暗黙的に割り当てられた記述子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 271d479a9d2faa8cd7ab01e02e830b194c4138b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300132"
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメント・ハンドルが割り振られている場合、アプリケーションは暗黙的に 4 つの記述子の 1 つのセットを割り振ります。 アプリケーションは、暗黙的に割り当てられたこれらの記述子のハンドルをステートメント・ハンドルの属性として取得できます。 アプリケーションは、ステートメント ハンドルを解放すると、ドライバーは、そのハンドル上のすべての暗黙的に割り当てられた記述子を解放します。
