---
title: "述語の制限事項と同様に |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5668f03e785c0d27133965f16af40ce69c2a2567
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-limitations"></a>述語の制限事項と同様に
列のデータが 255 文字より長い場合は、LIKE 比較は最初の 255 文字にのみ基づきます。  
  
 LIKE が使用されるプロシージャは定数パターンでのみサポートされます。 デスクトップ データベース ドライバーでは、パターンに一致するように SQL 92 をサポートします。  
  
 LIKE 述語にエスケープ句の使用はサポートされていません。  
  
 数値型または浮動小数点数のデータ型のデータを格納する列で LIKE 比較を実行できません必要があります。 結果は予測可能でない可能性があります。 詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。
