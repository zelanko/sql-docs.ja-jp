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
ms.openlocfilehash: 44da652ad1e52934fa48f32b1b2f88b30212ad3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083304"
---
# <a name="comparing-bookmarks"></a>ブックマークの比較
ブックマークはバイト比較可能であるため、等価性または非等値を比較できます。 これを行うために、アプリケーションは各ブックマークをバイトの配列として扱い、2つのブックマークを1バイトずつ比較します。 ブックマークは、結果セット内でのみ一意であることが保証されるため、異なる結果セットから取得されたブックマークを比較することは意味がありません。
