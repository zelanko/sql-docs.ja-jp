---
title: LIKE 述部の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d596d688956d7bdbf3d9125184d81c16249781c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298962"
---
# <a name="like-predicate-limitations"></a>LIKE 述語の制限事項
列のデータが 255 文字より長い場合、LIKE 比較は最初の 255 文字のみに基づいて行われます。  
  
 プロシージャで使用される LIKE は、定数パターンでのみサポートされます。 デスクトップ データベース ドライバは、SQL-92 LIKE パターン マッチングをサポートします。  
  
 LIKE 述部でのエスケープ節の使用はサポートされていません。  
  
 LIKE 比較は、数値データ型または浮動小数点データ型のデータを含む列に対して実行しないでください。 結果は予測できない場合があります。 詳細については、『 Microsoft *Jet データベース エンジン プログラマ ガイド 』* を参照してください。
