---
title: 述語の制限事項と同様に |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 891c6499f54c56635d74289517e8cf33f66ba4ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="like-predicate-limitations"></a>述語の制限事項と同様に
列のデータが 255 文字より長い場合は、LIKE 比較は最初の 255 文字にのみ基づきます。  
  
 LIKE が使用されるプロシージャは定数パターンでのみサポートされます。 デスクトップ データベース ドライバーでは、パターンに一致するように SQL 92 をサポートします。  
  
 LIKE 述語にエスケープ句の使用はサポートされていません。  
  
 数値型または浮動小数点数のデータ型のデータを格納する列で LIKE 比較を実行できません必要があります。 結果は予測可能でない可能性があります。 詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。
