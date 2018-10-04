---
title: 記述子を暗黙的に割り当てられた |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: fa25e99c5bc0b0a5799cfac479e97bd9b89db338
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811310"
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメント ハンドルが割り当てられるときに、アプリケーションは暗黙的に 4 つの記述子の 1 つのセットを割り当てます。 アプリケーションでは、ステートメント ハンドルの属性として記述子を暗黙的に割り当てられたこれらのハンドルを取得できます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルで暗黙的に割り当てられたすべての記述子を解放します。
