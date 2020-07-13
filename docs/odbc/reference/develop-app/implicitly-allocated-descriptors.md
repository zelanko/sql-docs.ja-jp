---
title: 暗黙的に割り当てられた記述子 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300132"
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメントハンドルが割り当てられると、アプリケーションは、4つの記述子のセットを暗黙的に割り当てます。 アプリケーションは、暗黙的に割り当てられたこれらの記述子のハンドルを、ステートメントハンドルの属性として取得できます。 アプリケーションがステートメントハンドルを解放すると、ドライバーはそのハンドルで暗黙的に割り当てられたすべての記述子を解放します。
