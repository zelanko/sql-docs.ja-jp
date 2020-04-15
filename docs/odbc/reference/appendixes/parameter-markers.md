---
title: パラメータマーカー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303573"
---
# <a name="parameter-markers"></a>パラメーター マーカー
SQL-92 仕様に従って、アプリケーションは次の場所にパラメーター マーカーを配置できません。 より包括的なリストについては、SQL-92 仕様を参照してください。  
  
-   **SELECT**リスト内  
  
-   *比較述部*の両方の*式*として  
  
-   二項演算子の両方のオペランドとして  
  
-   **BETWEEN**演算の第 1 オペランドと第 2 オペランドの両方として  
  
-   **BETWEEN**演算の最初と 3 番目のオペランドの両方として  
  
-   **IN**演算の式と最初の値の両方として  
  
-   単項 + または - 演算のオペランドとして  
  
-   *セット関数参照の*引数として  
  
 パラメーター・マーカーの詳細については、SQL-92 仕様を参照してください。 パラメータの詳細については、「ステートメント[パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。
