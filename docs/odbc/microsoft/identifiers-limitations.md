---
title: 識別子の制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c781113124d456e1ba866546d6ada7a17371d71f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208525"
---
# <a name="identifiers-limitations"></a>識別子の制限事項
スペースまたは特殊記号が識別子が含まれる場合は、バック引用符で囲まれた識別子を囲む必要があります。 有効な名前は、うち最初の文字することはできません、スペース、64 文字の文字列です。 有効な名前は、制御文字または特殊文字を含めることはできません: ' &#124; # * でしょうか。 [ ] . ! $ .  
  
 予約語に記載の付録 C での SQL 文法を使用しないでください、 *ODBC プログラマ リファレンス*(またはこれらの予約語の短い形式) として識別子 (つまり、テーブルまたは列名)、word の背面に囲まれている場合を除き、引用符 (')。
