---
title: "述語の制限事項と同様に |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cb55109261fee419af8bd0773ed8e85956e8ca9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="like-predicate-limitations"></a>述語の制限事項と同様に
列のデータが 255 文字より長い場合は、LIKE 比較は最初の 255 文字にのみ基づきます。  
  
 LIKE が使用されるプロシージャは定数パターンでのみサポートされます。 デスクトップ データベース ドライバーでは、パターンに一致するように SQL 92 をサポートします。  
  
 LIKE 述語にエスケープ句の使用はサポートされていません。  
  
 数値型または浮動小数点数のデータ型のデータを格納する列で LIKE 比較を実行できません必要があります。 結果は予測可能でない可能性があります。 詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。
