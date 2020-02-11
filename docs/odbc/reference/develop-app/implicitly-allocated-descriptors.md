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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0eb34866b75802a32c63e62b41d384e5a1dea73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138953"
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメントハンドルが割り当てられると、アプリケーションは、4つの記述子のセットを暗黙的に割り当てます。 アプリケーションは、暗黙的に割り当てられたこれらの記述子のハンドルを、ステートメントハンドルの属性として取得できます。 アプリケーションがステートメントハンドルを解放すると、ドライバーはそのハンドルで暗黙的に割り当てられたすべての記述子を解放します。
