---
title: ブックマークの比較 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307477"
---
# <a name="comparing-bookmarks"></a>ブックマークの比較
ブックマークはバイトに匹敵するため、等しいか、または不等式かどうかを比較できます。 これを行うには、アプリケーションは各ブックマークをバイト配列として扱い、2 つのブックマークをバイト単位で比較します。 ブックマークは結果セット内でのみ区別されるため、異なる結果セットから取得されたブックマークを比較しても意味がありません。
