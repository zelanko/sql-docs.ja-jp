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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307477"
---
# <a name="comparing-bookmarks"></a>ブックマークの比較
ブックマークはバイト比較可能であるため、等価性または非等値を比較できます。 これを行うために、アプリケーションは各ブックマークをバイトの配列として扱い、2つのブックマークを1バイトずつ比較します。 ブックマークは、結果セット内でのみ一意であることが保証されるため、異なる結果セットから取得されたブックマークを比較することは意味がありません。
