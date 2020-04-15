---
title: 拡張を設定して新しいデータ型を有効にするSQL |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b703c5c14c4743e13feee139d16e5dfeb3c24c63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303413"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>ExtendedAnsiSQL を設定して新しいデータ型の有効化
Jet 4.0 データベースでは、ExtendedAnsiSQL フラグがオンになっている場合、SQL_DECIMALとSQL_NUMERICの 2 つの新しいデータ型を使用できます。 デフォルトの精度と位取りは、それぞれ 18 と 0 です。 SQL_DECIMALまたはSQL_NUMERICとして入力された ODBC を使用してアクセスされるデータは、通貨ではなく Microsoft Jet Decimal にマップされます。  
  
 ExtendedAnsiSQL フラグがオフになっている場合、10 進数または数値型のテーブルを作成することはできません。 ただし、テーブルに新しいデータ型が含まれている場合は、正しいデータ型で使用できます。
