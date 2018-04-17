---
title: ブックマークを比較する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 44561e4386353ef1efaf3dd41e5a24b93941963d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="comparing-bookmarks"></a>ブックマークを比較します。
ブックマークがバイトを比較できるのでは、等値演算子または非等値の比較できます。 これを行うは、アプリケーションは、各ブックマークをバイト配列として扱われます、2 つのブックマークでバイトを比較します。 ブックマークの結果セット内でのみ一意では保証されているため、意味がありませんをそれぞれ異なる結果セットから取得したブックマークを比較します。
