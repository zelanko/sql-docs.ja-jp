---
title: 記述子ハンドルの取得 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8bfa0b36ecca3af655efde84c3ce3f22ab0c1f88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086314"
---
# <a name="obtaining-descriptor-handles"></a>記述子ハンドルの取得
アプリケーションは、明示的に割り当てられた記述子のハンドルを、 **SQLAllocHandle**への呼び出しの出力引数として取得します。 暗黙的に割り当てられた記述子のハンドルは、 **SQLGetStmtAttr**を呼び出すことによって取得されます。
