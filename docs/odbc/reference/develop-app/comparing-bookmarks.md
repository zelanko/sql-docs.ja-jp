---
title: ブックマークの比較 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 690acf80bfabdc04d5f70b780e41943337c18cb9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026607"
---
# <a name="comparing-bookmarks"></a>ブックマークの比較
ブックマークがバイトを比較できるため、等値または非等値比較できます。 これを行うには、アプリケーションは、各ブックマークをバイト配列として扱われます、2 つのブックマークのバイトを比較します。 ブックマークは、結果セット内でのみ一意では保証されているため意味がない別の結果セットから取得したブックマークを比較します。
