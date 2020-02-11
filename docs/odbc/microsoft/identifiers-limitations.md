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
ms.openlocfilehash: 251ae0e4e94cec903e2c4b5cf687ed9b8b41dfc8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952398"
---
# <a name="identifiers-limitations"></a>識別子の制限事項
識別子に空白または特殊な記号が含まれている場合は、識別子を逆引用符で囲む必要があります。 有効な名前は、64文字以内の文字列で、最初の文字をスペースにすることはできません。 有効な名前には、制御文字または次の特殊文字を含めることはできません: ' &#124; # *? [ ] . ! $ .  
  
 SQL の文法に記載されている予約語は、 *ODBC プログラマーズリファレンス*の付録 C (または、これらの予約語の短縮形) の識別子として使用しないでください (または、テーブル名または列名)。これは、単語を引用符 (') で囲む場合を除きます。
